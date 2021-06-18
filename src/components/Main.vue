<template>
  <div class="container">
    <div class="main">
      <div v-if="ideas.length < 6">
        <input type="text" @keypress="handlePush">
      </div>
      <div v-else>
        <span>Desculpe amigão, número de ideias excede a capacidade máxima de 5 ideias!</span>
      </div>
      <button @click="randomize">Gerar</button>
    </div>
    <ul class="bucket">
      <li v-for="idea in ideas.slice(0,6)" :key="idea.id">
        {{idea.content}}
      </li>
    </ul>
    <div class="choosen">{{choosen.content}}</div>
  </div>
</template>

<script>
  export default {
    name: 'Main',
    data: ()=>{
      return{
        ideas:[
          {
            id: null,
            content: null
          }
        ],
    
        nextId: 1,
    
        choosen: ''
      }    
    },
    
    methods:{
      handlePush(e){
        const input = document.querySelector('input');
        if(this.ideas.length < 6){
          if(e.keyCode === 13 && input.value){
            this.ideas.push({
              id: this.nextId++,
              content: input.value
            })
            input.value = '';
          }
        }
      },

      randomize(){
        let arrayToShuffle = [...this.ideas];
        this.shuffleArray(arrayToShuffle);
        this.choosen = arrayToShuffle[0];
        
        if(this.choosen.content == null){
          this.choosen = this.ideas[1];
        }

        return this.choosen;
      },
      
      shuffleArray(arr){
        for(let i = arr.length - 1; i > 0; i--){
          const j = Math.floor(Math.random() * (i + 1));
          [arr[i], arr[j]] = [arr[j], arr[i]];
        }
        return arr;
      }
    }
  }
</script>

<style>
.container, .container .main{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.container{
  width: 100%;
  color:aliceblue;
  text-shadow: 0 0 5px #C8C8C8;
  position:relative;
}

.container .main{
  margin-top: 10px;
}

.container .bucket{
  list-style: none;
  position: absolute;
  left: 0;
  bottom: -150px;
}

.container .bucket li{
  font-size: 2em;
  font-family: 'Roboto', sans-serif;
}

.container .main input{
  width: 20em;
  padding: 5px;
  background: #010a01;
  border: 3px solid #f09;
  border-radius: 8px;
  color: aliceblue;
  margin-right: 15px;
  font-weight: bold;
  font-size: 25px;
}

.container .main button{
  width: 10em;
  padding: 5px;
  font-size: 25px;
  background: transparent;
  border: 2px solid #0099FF;
  border-radius: 5px;
  color: #99FF00;
  margin-top: 15px;
  text-shadow: 0 0 3px #99FF00;
}

.container .main span{
  font-size: 24px;
  text-align: center;
  font-family: 'Roboto', sans-serif;
}

.container .main button:hover{
  border: 2px solid #003d66;
  color: #3d6600;
  cursor: pointer;
}

.container .choosen{
  font-size: 5em;
  text-shadow:
    0 0 calc(7px - 6px) #fff,
    0 0 calc(10px - 6px) #fff,
    0 0 calc(21px - 6px) #fff,
    0 0 calc(42px - 6px) #0fa,
    0 0 calc(82px - 6px) #0fa,
    0 0 calc(92px - 6px) #0fa,
    0 0 calc(102px - 6px) #0fa,
    0 0 calc(151px - 6px) #0fa;
  }

@media screen and (max-width: 800px){
  .container, .container .main{
    flex-direction: column;
  }

  .container .main button{
    margin-top: 10px;
  }

  .container .bucket{
    font-size: 14px;
    
  } 
}

@media screen and (max-width: 600px) {
  .container .main input{
    font-size: 10px;
  }

  .container .main button{
    font-size: 14px;
  }

  .container .bucket li{
    font-size: 1.5em;
    position: relative;
    bottom: -100px;
    
  }

  .container .choosen{
    font-size: 3em;
    height: 40px;
  }
}
</style>