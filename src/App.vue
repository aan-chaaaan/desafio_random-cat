<template>
  <div id="App">
    <h1 class="title">Random Gif Cat</h1>
    <div class="container_dad">
      <div class="container">
        <form @submit.prevent="createNewCat()">
          <h3>Titulo</h3>
          <input type="text" v-model="form.selectTitle" />

          <h3>Filtro</h3>
          <select
            name="select"
            id="Filter"
            v-model="form.selectFilter"
            required
          >
            <option value="blur">blur</option>
            <option value="mono">mono</option>
            <option value="sepia">sepia</option>
            <option value="negative">negative</option>
            <option value="paint">paint</option>
            <option value="pixel">pixel</option>
          </select>

          <h3>Color</h3>
          <select name="select" id="Colour" v-model="form.selectColor" required>
            <option value="blue">blue</option>
            <option value="red">red</option>
            <option value="pink">pink</option>
            <option value="green">green</option>
            <option value="coral">coral</option>
          </select>
          <div
            class="circulito"
            :style="{ 'background-color': form.selectColor }"
          ></div>

          <h3>Tamaño</h3>
          <input
            type="number"
            v-model="form.selectSize"
            step="100"
            min="100"
            max="500"
            v-model.number="form.selectSize"
          />
          <button type="submit">Obtener mi gatito</button>
        </form>
      </div>
    </div>

    <img :src="urlcat" alt="cat-image" class="cat_image" />
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    urlcat: "",
    form: {
      selectTitle: null,
      selectFilter: null,
      selectColor: null,
      selectSize: null,
    },
  }),
  methods: {
    createNewCat() {
      this.urlcat = `https://cataas.com/cat/gif/says/${this.form.selectTitle}?filter=${this.form.selectFilter}&color=${this.form.selectColor}&width=${this.form.selectSize}&height=${this.form.selectSize}`;
    },
  },
};
</script>

<style scoped>
body,
html {
  margin: 0;
}
#App {
  background-color: rgb(170, 212, 212);
  width: 1350px;
  height: 800px;
}
.title {
  margin: 0;
  padding-top: 20px;
  text-align: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.container_dad {
  width: 1350px;
  background-color: rgb(219, 130, 148);
}
.container {
  width: 250px;
  margin-top: 40px;
  margin-left: 570px;
}

h3 {
  margin: 20px;
  display: inline-block;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 300;
}
#Title {
  width: 80px;
  margin: 15px;
}
#Filter {
  width: 100px;
  margin: 20px;
}
#Colour {
  width: 100px;
  margin: 15px;
}
#Size {
  width: 80px;
}
button {
  width: 150px;
  margin: 20px;
  margin-left: 50px;
  height: 40px;
  background-color: indianred;
  border-radius: 10%;
  color: white;
  font-size: 14px;
}
.cat_image {
  margin-left: 550px;
  padding-top: 20px;
}
.circulito {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  display: inline-block;
}
</style>
