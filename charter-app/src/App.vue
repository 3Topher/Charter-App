<template>
  <div id="app" class="mt-3">

    <b-navbar type="dark" variant="info">
      <b-navbar-nav>
        <b-nav-item href="#">Home</b-nav-item>

        <!-- Navbar dropdowns -->
        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">ES</b-dropdown-item>
          <b-dropdown-item href="#">RU</b-dropdown-item>
          <b-dropdown-item href="#">FA</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item-dropdown text="User" right>
          <b-dropdown-item href="#">Account</b-dropdown-item>
          <b-dropdown-item href="#">Settings</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-navbar>

    <b-table striped hover :items="items"></b-table>

    <b-button-group>

      <b-dropdown right text="Choose Customer">
        <b-dropdown-item v-for="item in items" @click="buttonSelect = item.id" :key="item.first_name">{{ item.first_name
        }}</b-dropdown-item>
      </b-dropdown>


      <b-dropdown right text="Choose Item">
        <b-dropdown-item v-for="item in items2" @click="pointValue = pointCalc(item.price)" :key="item.name">{{
            item.name
        }}</b-dropdown-item>
      </b-dropdown>

      

      <b-button @click="items[buttonSelect].points += pointValue">Purchase</b-button>
      <b-button variant="warning" @click="items[buttonSelect].points = 0">Reset Points</b-button>
    </b-button-group>

    <b-table striped hover :items="items2"></b-table>

  </div>
</template>

<script>
export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      items: [
        { points: 0, first_name: 'Meyer', last_name: 'Macdonald', id: 0 },
        { points: 0, first_name: 'Larsen', last_name: 'Shaw', id: 1 },
        { points: 0, first_name: 'Geneva', last_name: 'Wilson', id: 2 },
        { points: 0, first_name: 'Jami', last_name: 'Carney', id: 3 }
      ],
      items2: [
        {
          "name": "Shirt",
          "price": 120,
          "id": 0
        },
        {
          "name": "Shoes",
          "price": 60,
          "id": 1
        },
        {
          "name": "Hat",
          "price": 20,
          "id": 2
        }
      ],
      buttonSelect: 0,
      pointValue: 0,
      numberVal: 0

    }
  },
  methods: {
    pointCalc(spent) {
      let points = spent - 100;
      let pointsTwo = spent - 50;
      let pointsTotal = points * 2;
      let pointsAdded = pointsTotal + pointsTwo;

      if (spent > 100) {
        return pointsAdded;
      } else if (spent > 50) {
        return pointsTwo;
      } else {
        return 0;
      }
    }
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
</style>
