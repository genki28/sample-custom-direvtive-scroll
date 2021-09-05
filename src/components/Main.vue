<template>
  <div>
    <div v-for="animal in animals" :key="animal.id">ID:{{animal.id}} name:{{animal.name}}</div>
    <div v-animal-scroll="infiniteHandler"></div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {
      animals: [],
      animalData: [],
      start: 0,
      end: 40,
      // データ更新を行うスクロール量
      startScrollYOffset: 0
    }
  },
  mounted() {
    const list = ['サーバル', 'フェネック', 'アライグマ', 'カバ', 'コツメカワウソ', 'ジャガー', 'トキ']
    for(let i = 0; i < 200; i++) {
      this.animalData.push({id: i, name: list[Math.floor(Math.random()*list.length)]})
    }
    this.startScrollYOffset = Math.floor(window.innerHeight / 3)
    this.getAnimals()
  },
  methods: {
    infiniteHandler() {
      // 現時点でのスクロール量が取得を行うスクロール量以上
      if (window.pageYOffset >= this.startScrollYOffset) {
          this.startScrollYOffset = window.innerHeight + window.pageYOffset
          this.getAnimals()
      }
    },
    // axiosとかのAPIの想定
    getAnimals() {
      if (this.end <= this.animalData.length) {
        this.animals = this.animals.concat(this.animalData.slice(this.start, this.end))
        this.start = this.start + 40
        this.end = this.end + 40
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>