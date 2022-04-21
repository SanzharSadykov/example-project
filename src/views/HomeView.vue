<template>
  <div class="home" :style="bgObject">
    <div class="container mx-auto">
      <button @click="changeBG()" class="col-button w-1/4 text-center rounded-lg text-lg border-2 border-black shadow-2xl">Нажми меня, чтобы изменить цвет фона</button>
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
    }
  },
  name: 'HomeView',
  components: {
  },
  methods: {
    changeBG() {
      document.body.classList.remove(this.colorClass);
      this.colorClass = 'bg-' + this.colors[Math.floor(Math.random(this.colors.length+1) * 10)] + '-' + Math.floor(Math.random(1,11) * 10)*100;
      document.body.classList.add(this.colorClass);
      console.log("Successfully changed BG color to: " + this.colorClass);
    }
  },
  mounted() {
    this.colorClass = 'bg-' + this.colors[Math.floor(Math.random(this.colors.length+1) * 10)] + '-' + Math.floor(Math.random(1,11) * 10)*100;
    document.body.classList.add(this.colorClass);
  }
}
</script>
