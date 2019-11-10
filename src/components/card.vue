<template>
  <div class="cards">
    <div class="btn-add" @click="isModal = !isModal">+</div>

    <div class="wrap">
      <div 
        class="card" 
        v-for="(c, i) in getCard" 
        :key="i">
        <div class="front" :style="{backgroundImage : c.image}"></div>
        <div class="back" :style="{backgroundImage : c.backImage}">
          <span>{{c.name}}</span>
        </div>
      </div>
    </div>

    <div class="modal__bg" v-if="isModal">
      <div class="modal">
        <h3>Добавить карточку</h3>
        <div>
          <label>URL</label>
          <input type="text" placeholder="URL" v-model="url">
        </div>

        <div>
          <label>Name</label>
          <input type="text" placeholder="Name" v-model="name">
        </div>
        <button @click="add()">add</button>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      url: "",
      name: "",
      isModal: false,
      card: [
        {
          name: "dog",
          image: "https://www.medicalnewstoday.com/content/images/articles/322/322868/golden-retriever-puppy.jpg"
        },
        {
          name: "2",
          image: "https://www.medicalnewstoday.com/content/images/articles/322/322868/golden-retriever-puppy.jpg"
        },
        {
          name: "3",
          image: "https://www.medicalnewstoday.com/content/images/articles/322/322868/golden-retriever-puppy.jpg"
        },
      ]
    }
  },
  computed: {
    getCard(){
      let c = [];
      for(let i of this.card){
        let j = {
          name : i.name,
          image: "url("+i.image+")",
          backImage : "linear-gradient(0deg, rgba(0,0,0,0.6), rgba(0,0,0,0.6))," + "url("+i.image+")"
        }
        c.push(j)
      }
      return c
    }
  },
  methods: {
    add(){

      this.card.push({name : this.name, image : this.url});
      this.isModal = false;
    }
  }
}
</script>

<style scoped>

.btn-add{
  position: fixed;
  right: 50px;
  bottom: 25px;
  width: 64px;
  height: 64px;
  border: none;
  background: #6b38fb;
  border-radius: 50%;
  font-size: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  cursor: pointer;
  transition: 0.1s;
  z-index: 10;
}
.btn-add:hover{
  background: #5429cc;
}
.btn-add:active{
  bottom: 23px;
}


.wrap {
  position: relative;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
/*  background-color: #BBDEFB;*/
  display: flex;
  flex-wrap: wrap;
  border-radius: 10px;
  padding: 25px;
  box-sizing: border-box;
}
.card {
  width: 250px;
  height: 300px;
  position: relative;
  perspective: 1000px;
  border-radius: 10px;
  margin: 15px;
  
}
.front, .back {
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: 1s;
  backface-visibility: hidden;
  border-radius: 10px;
  cursor: pointer;
  background-size: cover;
  background-position: center center;

}
.front {
  background-color: #ccc;
  box-shadow: 2px 4px 6px #00000040;
}
.back {
  background-color: #BDBDBD;
  transform: rotateY(180deg);
  box-shadow: -2px 4px 6px #00000040;
  color: #fff;
  font-size: 20px;
}
.card:hover .front {transform: rotateY(180deg);}
.card:hover .back {transform: rotateY(360deg);}

.modal__bg{
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(0deg, rgba(0,0,0,.7), rgba(0,0,0,.7));
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal{
  background: #fff;
  padding: 25px 50px;
  box-shadow: 0 2px 4px #00000040;
  border-radius: 4px;
}

</style>
