<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="filter-wrapper">
          <div class="left-side filter">
            <input type=" text" v-model="search" placeholder="Search Furtniture" />
            <span class="filter-checkbox">
              <!-- <input type=" text" v-model="search" placeholder="Furtniture Style" /> -->
              <div class="dropdown filter-white">
                <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  Furtniture Style
                </button>
                <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check1">Classic</label>
                      <input type="checkbox" class="form-check-input" id="Check1">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check2">Midcentury</label>
                      <input type="checkbox" class="form-check-input" id="Check2">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check3">Scandinavian</label>
                      <input type="checkbox" class="form-check-input" id="Check3">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check4">Modern</label>
                      <input type="checkbox" class="form-check-input" id="Check4">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check5">Contemporary</label>
                      <input type="checkbox" class="form-check-input" id="Check5">
                    </div>
                  </a>
                </div>
              </div>
            </span>
          </div>
          <div class="right-side filter">
            <span class="filter-dropdown">
                <div class="dropdown filter-white filter-checkbox">
                  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Delivery Time
                  </button>
                  <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">

                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check1">1 Week</label>
                      <input type="checkbox" class="form-check-input" id="Check1">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check2">2 Week</label>
                      <input type="checkbox" class="form-check-input" id="Check2">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check3">1 Month</label>
                      <input type="checkbox" class="form-check-input" id="Check3">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check4">2 Month</label>
                      <input type="checkbox" class="form-check-input" id="Check4">
                    </div>
                  </a>
                  <a class="dropdown-item" href="#">
                    <div class="form-check">
                      <label class="form-check-label" for="Check5">3 Month</label>
                      <input type="checkbox" class="form-check-input" id="Check5">
                    </div>
                  </a>
                  </div>
              </div>
            </span>
          </div>
        </div>
        <div class="listing-wrapper">
          <!-- <ul>
            <li v-for="products in filterProducts" :key="products" class="card">
              <span class="top">
                <h3>{{ products.name }}</h3>
                <h5>{{ products.price }}</h5>
              </span>
              <p>{{ products.description }}</p>
              <p class="blue-text">{{ products.furniture_style }}</p>
              <p class="right">{{ products.delivery_time }}</p>
            </li>
          </ul> -->
          <div class="row">
          <div v-for="products in filterProducts" :key="products" class="col-sm-6 col-xs-12">
            <div class="card">
              <span class="top">
                <h3>{{ products.name }}</h3>
                <h5>{{ products.price }}</h5>
              </span>
            <p>{{ products.description }}</p>
            <span>
              <label>Furtniture Style</label>
              <p class="blue-text">{{ products.furniture_style }}</p>
            </span>
            <span class="right">
              <label>Delivery Time</label>
              <p>{{ products.delivery_time }} Week</p>
            </span>

            </div>
          </div>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios' 
  export default {
    name: 'App',
      data () {
      return {
      products: [],
      search: ''
      }
    },
    mounted() {
      axios.get("http://www.mocky.io/v2/5c9105cb330000112b649af8")
      .then(response => {this.products = response.data.products})
    },
    computed:{
      filterProducts: function(){
        return this.products.filter((products) =>{
        return products.name.match(this.search);
        });
      }
    }
  } 
</script>
<style lang="scss">
  @import './assets/styles/custom.scss';
  @import "../node_modules/bootstrap/scss/bootstrap.scss";

  #app {
    font-family: 'Montserrat', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
      .filter-wrapper {
          width: 100%;
          background: #0087bb;
          padding: 20px;
          .filter {
              width: 50%;
              text-align: left;
              padding: 20px;
              display: inline-block;
              input {
                  background: transparent;
                  color: #fff;
                  box-shadow: none;
                  border: 0;
                  border-bottom: 1px solid white;
                  width: 100%;
                  outline: none;
              }
              .filter-white {
                  .btn {
                    width: 100%;
                    text-align: left;
                    background: #fff !important;
                    border-radius: 0;
                    border: 0;
                    margin-top: 25px;
                    color: #655f5f;
                    font-size: 17px !important;
                    display: flex;
                    align-items: center;
                    &:after{
                      margin-left: auto;
                    }
                  }
                  .dropdown-menu {
                      width: 100%;
                      border-radius: 0;
                  }
              }
          }
          .filter-checkbox .form-check {
            display: flex;
            padding: 0;
            input {
                width: 20px;
                margin-left: auto !important;
                position: relative;
            }
        }
      }
      .listing-wrapper {
            border: 1px solid #333;
            border-top: 0;
            .row{
              margin: 0;
              .card {
                  padding: 20px;
                  text-align: left;
                  margin-top: 30px;
                  .top {
                      display: flex;
                      h3 {
                          font-size: 25px;
                          font-weight: 700;
                      }
                      h5 {
                          margin-left: auto;
                          font-size: 18px;
                          color: orange;
                          font-weight: 600;
                      }
                  }
                  p{
                    font-size: 16px;
                    color: #656262;
                  }
                  .blue-text{
                    color: #0087bb;
                  }
                  .right{
                    text-align: right;
                    p{
                      color: blue;
                      text-decoration: underline;
                      font-weight: 600;
                    }
                  }
              }
            }
      }
  }

  #nav {
    padding: 30px;

    a {
      font-weight: bold;
      color: #2c3e50;

      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }

</style>
