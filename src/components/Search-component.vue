
<template>
  <div>
    <div class="search-box__container">
      <input
          v-model="search"
          @keyup.enter="trigger"
          type="text"
      />
      <button
          class="search-box__button"
          type="button"
          @click="onChange"
          ref="getProducts"
      >Search</button>
    </div>

    <ul
        class="autocomplete-results"
    >
      <li
          v-for="(result, i) in results"
          :key="i"
          @click="setResult(result)"
          class="autocomplete-result"
      >
        <strong>{{ result.brand }}</strong> - {{ result.name }}
      </li>
    </ul>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Search-component',
  data() {
    return {
      search: '',
      products: null,
      results: []
    };
  },
  created() {
    axios.get(`https://thawing-scrubland-03171.herokuapp.com/https://skincare-api.herokuapp.com/product?q=cream`)
        .then(response => {
          // JSON responses are automatically parsed.
          this.products = response.data
        })
        .catch(e => {
          this.errors.push(e)
        });
  },
  methods: {
    // filter results when some change is made in input
    filterResults() {
      this.results = this.products.filter(item => item.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1);
    },
    onChange() {
      this.filterResults();
    },
    setResult(result) {
      this.search = result;
    },
    trigger () {
      this.$refs.getProducts.click();
    }
  }
}
</script>

<style >

.search-box__container {
  display: grid;
  grid-template-columns: 80% 1fr;
  gap: 10px;
}

.search-box__container input {
  height: 40px;
  border-radius: 6px;
  outline: none;
  border: 1px solid grey;
  padding: 10px;
}

.search-box__button {
  padding: 6px;
  background-color: #55D7FF;
  border: 1px solid grey;
  border-radius: 6px;
  font-size: 1em;
  outline: none;
  cursor: pointer;
}

.search-box__button:hover {
  background-color: #4ad2fa;
}

.autocomplete-results {
  margin-top: 20px;
  padding: 0 16px;
  color: white;
}

@media (min-width: 768px) {
  .search-box__container {
    gap: 18px;
  }

  .search-box__container,
  .autocomplete-results {
    margin: 0 auto;
    max-width: 50vw;
  }

  .autocomplete-results {
    margin-top: 20px;
    line-height: 1.2em;
  }
}

@media (min-width: 1025px) {
  .search-box__container {
    gap: 16px;
  }
}
</style>