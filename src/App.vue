<template>
	<div id="app">
		
		<span id="title">Show your <b>CONQUEST!</b></span>
		<div id="mySelect">
			<v-select label="name" :options="countries" v-model="selected" placeholder="Insert a country you have visited!"></v-select>
			<button @click="addToVisited(selected)">Add</button>
			<button @click="removeFromVisited(selected)">Remove</button>
		</div>
		<WorldMap :visitedCountries="visitedCountries"></WorldMap>

		<span id="signature"><b>Renato Henriques</b>, <i>a boy who should be studying</i></span>
	</div>
</template>

<script>
import WorldMap from './components/WorldMap.vue';
import vSelect from "vue-select";
import Countries from "./countries.js";

export default {
	components: {
		WorldMap,
    "v-select": vSelect
  },
  data() {
    return {
      countries: Countries,
			visitedCountries: {},
      selected: null
    };
  },
  methods: {
		addToVisited(country) {
			this.$set(this.visitedCountries,country.code, 500);

			this.selected = null;
		},
		removeFromVisited(country) {
			this.$delete(this.visitedCountries,country.code);

			this.selected = null;
		}
	}
}
</script>

<style>

body {
  background-color: skyblue;
}

#mySelect {
	position: fixed;
	top: 0;
  right: 0;
	width: 30%;
}

#title {
	position: fixed;
	top: 0;
  left: 0;
	font-style: italic;
	font-size: 1.875em;
}

#signature {
	position: fixed;
	bottom: 0;
  right: 0;
	font-size: 0.895em;
}

</style>