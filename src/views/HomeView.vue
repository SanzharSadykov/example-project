<template>
  <div class="home">
    <div class="container mx-auto">
      <button @click="changeBG()" class="font-semibold col-button w-1/4 text-center rounded-lg text-lg border-2 border-black shadow-2xl">Нажми меня, чтобы изменить цвет фона</button>
      <div @click="displayAnswer(quiz.id-1)" class="shadow-xl w-1/2 mx-auto bg-white rounded-lg text-black font-semibold text-lg" v-for="quiz in quizData" :key="quiz">
        <p class="p-1 mt-2 text-black text-lg font-bold">{{quiz.id + '. ' + quiz.q}}</p>
        <p v-if="quiz.clicked === true" class="p-1 mb-2 text-black text-lg font-semibold"><span class="text-red-500 text-lg font-bold">Ответ:</span> {{quiz.a}}</p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      colors: ['slate','gray','zinc','neutral','stone','red','orange','amber','yellow','lime','green','emerald','teal','cyan','sky',
      'blue','indigo','violet','purple','fuchsia','pink','rose'],
      colorClass: '',
      colorNum: 0,
      quizData: [
        {
          "id": 1,
          "q": "Представьте, что вы находитесь в комнате, которая быстро наполняется водой. Здесь нет ни окон, ни дверей. Как вы выберетесь отсюда?",
          "a": "Перестаньте представлять этот сценарий.",
          "clicked": false
        },
        {
          "id": 2,
          "q": "Шли два отца и два сына, нашли три апельсина. Стали делить - всем по одному досталось. Как это могло быть?",
          "a": "На самом деле шло трое человек: дедушка, отец и сын.",
          "clicked": false
        },
        {
          "id": 3,
          "q": "Что принадлежит вам, но используется всеми остальными больше, чем вами?",
          "a": "Ваше имя.",
          "clicked": false
        },
        {
          "id": 4,
          "q": "Что полно дыр, но все еще может удерживать жидкость?",
          "a": "Губка.",
          "clicked": false
        },
        {
          "id": 5,
          "q": "Как вы называете женщину, которая все время знает, где находится ее муж?",
          "a": "Вдовой.",
          "clicked": false
        }                    
      ]
    }
  },
  name: 'HomeView',
  components: {
  },
  methods: {
    changeBG() {
      document.body.classList.remove(this.colorClass);
      this.colorNum = Math.floor(Math.random(1,11) * 10)*100;
      if (this.colorNum === 0) {
        this.colorNum = 50;
      }     
      this.colorClass = 'bg-' + this.colors[Math.floor(Math.random(this.colors.length+1) * 10)] + '-' + this.colorNum;
      document.body.classList.add(this.colorClass);
      console.log("Successfully changed BG color to: " + this.colorClass);
    },
    displayAnswer(id) {
      if (this.quizData[id].clicked === true) {
        this.quizData[id].clicked = false;
      } else {
        this.quizData[id].clicked = true;
      }
    }
  },
  mounted() {
    this.colorNum = Math.floor(Math.random(1,11) * 10)*100;
    if (this.colorNum === 0) {
      this.colorNum = 50;
    }
    this.colorClass = 'bg-' + this.colors[Math.floor(Math.random(this.colors.length+1) * 10)] + '-' + this.colorNum;
    document.body.classList.add(this.colorClass);
    document.body.classList.add('transition-all');
  }
}
</script>
