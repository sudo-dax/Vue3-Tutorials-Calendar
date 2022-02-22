<template>
  <div class="m-auto">
      <h1 class="text-2xl text-center font-bold underline">DC Heros {{ herosCount }}</h1>

      <ul>
        <li class="flex justify-between" v-for="(hero, index) in heros" :key="index">
          <div>
            {{ hero.name }} 
          </div>
            <button @click="remove(index)"> x </button>
        </li>
      </ul>

      <form class="mt-5 flex space-x-4" @submit.prevent="addHero">
        <input class="border rounded" v-model.trim.lazy="newHero" placeholder="       Enter Hero Name" />
        <button class="bl-2 p-1 border rounded bg-gradient-to-t from-red-400 to-pink-300" type="submit">Add Hero</button>
      </form>
    </div>
</template>

<script>
export default {
      computed: {
    herosCount() {
      return this.heros.length;
    },
  },

  methods: {
    addHero() {
      if (this.newHero !== "") {
        this.heros.unshift({ name: this.newHero });
        // console.log(this.newHero);
        // alert(`${this.newHero} is added`);
        this.newHero = "";
      }
    },

    remove(index) {
      this.heros = this.heros.filter((hero, i) => i != index)

    }
  },
  
data() {
    return {
      isDisabled: false,
      newHero: "",
      heros: [
        { name: "SuperGirl" },
        { name: "Flash" },
        { name: "Arrow" },
        { name: "Batman" },
        { name: "Superman" },
      ],
    };
  },
}
</script>

<style>

</style>