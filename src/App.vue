<template>
  <div class="container">
    <div class="wrapper">
      <div class="row" v-if="products.length">
        <div class="prodCard" v-for="product in products" :key="product.id">
          <div class="card-header">
            <h3>{{ product.prodName }}</h3>
          </div>
          <div class="card-body">
            <!-- Attribute binding - - is assigning a product value to an attribute -->
            <img :src="product.image" :alt="product.prodName" loading="lazy"  @mouseenter="onMouseEnter"
              @mouseleave="onMouseLeave">
            <p :class="product.amount > 420 ? 'expensive' : 'cheap'">R{{ product.amount.toFixed(2) }}</p>
            <p :class="product.id % 2 ==0 ? 'red' : 'blue'">R{{ product.amount.toFixed(2) }}</p>

          </div>
          <div class="card-footer">
            <a href="#" type="button">View Details</a>
          </div>
        </div>

      </div>
      <div v-else>
       <h2>Yoo</h2>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  // name: 'ProductsComp',
  data() {
    return {
      products: [
        {
          id: 1,
          prodName: 'Python Crash Course',
          category: 'Python',
          amount: 400.9999,
          image: 'https://i.postimg.cc/MKDLBPYm/Python-Crash-Course-cover.jpg'
        },
        {
          id: 2,
          prodName: 'Python Programming',
          category: 'Python',
          amount: 900.4586,
          image: 'https://i.postimg.cc/rFcbKX5p/Python-Programming-for-Beginners-cover.jpg'
        },
        {
          id: 3,
          prodName: 'Mastering C++',
          category: 'C++',
          amount: 1800.896,
          image: 'https://i.postimg.cc/Ss9zrpfT/Mastering-C-Programming.jpg'
        },
      ]
    }
  },
  computed() { },
  methods: {
    onMouseEnter() {
      alert('Hello there')
    },
    onMouseLeave() {
      alert('Bye')
    },
    // Can I add the color on the mouse leave
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.prodCard {
  width: 18rem;
}

.prodCard :is(>*, img) {
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: darkkhaki;
}
.red{
  background-color: red;
}
.blue{
  background-color: blue;
  box-shadow: 1vw .1vw .1vw .1vw ;
}

.cheap {
  color: black;
}</style>
