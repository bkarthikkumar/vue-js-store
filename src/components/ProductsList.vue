<template>
  <div class="row">
    <div class="col-xs-10 col-sm-3">
      <div class="form-group">
        <h3 for="category-filter-label">Filter</h3>
        <select
          class   = "form-control"
          name    = "categories-selector"
          id      = "category-filter"
          @change = "onChange($event)"
          v-model = "key"
        >
          >
          <option disabled value="">Select Category</option>
          <option
                        v-for = "(category, index) in categories"
                      :key    = "index"
                      :value  = "category"
          >
            {{ category }}
          </option>
        </select>
      </div>
    </div>
    <div class="col-xs-10 col-sm-7">
      <h3>Product List</h3>
      <div class="hello">
        <!-- <textarea v-model="listDataString" rows="20" cols="80"></textarea> -->
        <div class="container-fluid d-flex justify-content-center">
          <div class="row mt-5">
            <div
                          v-for = "(item, index) in listData"
                        :key    = "index"
                          class = "col-sm-4"
            >
              <div class="card">
                <img :src="item.image" class="card-img-top" width="100%" />
                <div class="card-body pt-0 px-0">
                  <div
                    class = "d-flex flex-row justify-content-between mb-0 px-3"
                  >
                    <small class="text-muted mt-1">Price: </small>
                    <h6>{{ item.price }}</h6>
                  </div>
                  <hr class="mt-2 mx-3" />
                  <div
                    class = "d-flex flex-row justify-content-between px-3 pb-4"
                  >
                    <div class="d-flex flex-column">
                      <span class="text-muted">Category</span>
                    </div>
                    <div class="d-flex flex-column">
                      <h5 class="mb-0">{{ item.category }}</h5>
                    </div>
                  </div>
                  <div class="d-flex flex-row justify-content-between p-3 mid">
                    <div class="d-flex flex-column">
                      <small class="text-muted mb-1">Description</small>
                      <div class="d-flex flex-row">
                        <div class="d-flex flex-column ml-1">
                          <p>{{ item.description }}</p>
                        </div>
                      </div>
                    </div>
                  </div>
                  <small class="text-muted key pl-3"> </small>
                  <div class="mx-3 mt-3 mb-2">
                    <button type="button" class="btn btn-danger btn-block">
                      <small>Add To Cart</small>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "Prod List",
  data() {
    return {
      listDataString: String,
      listData      : [],
      categories    : [],       // placeholder
    };
  },methods: {
        onChange(event) {
            console.log()
            axios
            .get("https://fakestoreapi.com/products/category/"+event.target.value)
            .then((response) => {
                this.listDataString = JSON.stringify(response.data, null, "\t");
                this.listData       = response.data;
                console.log(this.listDataString);
                return response; // multiline arrow function must return
            });
        }
    },
  mounted() {
    axios.get("https://fakestoreapi.com/products").then((response) => {
      this.listDataString = JSON.stringify(response.data, null, "\t");
      this.listData       = response.data;
      console.log(this.listDataString);
      return response; // multiline arrow function must return
    });
    axios
      .get("https://fakestoreapi.com/products/categories")
      .then((response) => {
        this.listDataString = JSON.stringify(response.data, null, "\t");
        this.categories     = response.data;
        console.log(this.listDataString);
        return response; // multiline arrow function must return
      });
  },
};
</script>
<style scoped>
.card {
  width        : 250px;
  border-radius: 10px;
}

.card-img-top {
  border-top-right-radius: 10px;
  border-top-left-radius : 10px;
  width                  : 100%;
  height                 : 15vw;
  object-fit             : cover;
}

span.text-muted {
  font-size: 12px;
}

small.text-muted {
  font-size: 8px;
}

h5.mb-0 {
  font-size: 1rem;
}

small.ghj {
  font-size: 9px;
}

.mid {
  background: #ecedf1;
}

h6.ml-1 {
  font-size: 13px;
}

small.key {
  text-decoration: underline;
  font-size      : 9px;
  cursor         : pointer;
}

.btn-danger {
  color: #ffcbd2;
}

.btn-danger:focus {
  box-shadow: none;
}

small.justify-content-center {
  font-size      : 9px;
  cursor         : pointer;
  text-decoration: underline;
}

@media screen and (max-width: 600px) {
  .col-sm-4 {
    margin-bottom: 50px;
  }
}
</style>