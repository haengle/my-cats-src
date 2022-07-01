<script>
  import { myCats } from '../data/cats';
  import draggable from 'vuedraggable'

  export default {
    components: {
      draggable
    },
    data() {
      return {
        list1: myCats,
        list2: this.getColors()
      };
    },
  methods: {
  
    getColors: function() {
      const catColors = [...myCats];
      function shuffleArray(inputArray){
        return inputArray.sort(()=> Math.random() - 0.5);
      }
        return shuffleArray(catColors);
    },

    checkMatches: function() {
       const check1 = JSON.stringify(this.list1);
       const check2 = JSON.stringify(this.list2);

       if (check1 === check2) {
        alert('Congrats, you are also a crazy cat person')
       } else {
        alert('Wrong, try again :P')
       }
    }
  }
};

</script>

<template>
<header>
    <h1>Match the cats</h1>
    <a href="/" class="button">My Cats</a>
  </header>
  <p><strong>Sort the lists to match the cat to their color, then hit the "Check Answers" button to see if you were right</strong></p>
  <hr/>
  <div class="match-wrapper">

    <div class="match-list">
      <h3>Names</h3>
      <draggable
        class="dragArea list-group"
        :list="list1"
        group="names"
        item-key="name"
      >
        <template #item="{ element }">
          <div class="list-group-item">
            {{ element.name }}
          </div>
        </template>
      </draggable>
    </div>

    <div class="match-list">
      <h3>Colors</h3>
      <draggable
        class="dragArea list-group"
        :list="list2"
        group="colors"
        @change="log"
        item-key="name"
      >
        <template #item="{ element }">
          <div class="list-group-item">
            {{ element.color }}
          </div>
        </template>
      </draggable>
    </div>
  </div>

  <a class="button mt-8" @click="checkMatches">Check Answers</a>
</template>

<style scoped>

.match-wrapper {
  display: flex;
  margin-top: 2rem;
}

.match-list {
  flex: 0 1 45%;
}

.list-group-item {
  padding: 1rem 0;
  border-bottom:1px solid #f4f4f4
}

.mt-8 {
  margin-top: 2rem;
}

</style>
