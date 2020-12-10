<template>
  <div class="product-challange-wrapper">
    <h4 class="page-title">XYZ SOLUTIONS</h4>
    <div>Product Challange</div>
    <input type="text" placeholder="Search..." class="search-input-box" v-model="searchVal" />
    <ul>
      <li v-for="(item, index) in filteredItems" :key="index" class="user-list-item">
        <div class="img-box">
          <img src="../assets/220x220.png" alt="User-Image"/>
        </div>
        <div class="user-details-box">
          <div class="user-name">{{item.name}}</div>
          <div class="user-email">{{item.emailId}}</div>
        </div>
      </li>
    </ul>
    <div v-if="!filteredItems.length" class="error-box">{{errorMessage}}</div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      searchVal: "",
      errorMessage: "No Result Found!",
      users: [
        {
          name: "Michael Lawson",
          emailId: "michael.lawson@reqres.in"
        },
        {
          name: "John Doe",
          emailId: "john.doe@reqres.in"
        },
        {
          name: "MS Dhoni",
          emailId: "ms.dhoni@reqres.in"
        },
        {
          name: "Rahul Dravid",
          emailId: "rahul.dravid@gmail.com"
        }
      ]
    }
  },
  computed: {
    filteredItems() {
      return this.users.filter(user => {
        return user.name.toLowerCase().indexOf(this.searchVal.toLowerCase()) > -1;
      });
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0;
}

.product-challange-wrapper {
  text-align: center;
  max-width: 500px;
  margin: 30px auto;
  padding: 0 20px;
}
.page-title {
  text-transform: uppercase;
  margin: 0;
}
.search-input-box {
  width: 100%;
  height: 40px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 15px;
  padding: 10px;
}
.user-list-item {
  display: flex;
  align-items: center;
  text-align: left;
  border: 1px solid #000;
  border-radius: 5px;
  margin-bottom: 10px;
  padding: 10px;
}
.user-details-box {
  margin-left: 10px;
}
.img-box {
  width: 50px;
  height: 50px;
}
.img-box img {
  width: 100%;
  border-radius: 100%;
}
.user-name {
  font-weight: bold;
  margin-bottom: 10px;
}
.error-box {
  color: #856404;
  background-color: #fffaeb;
  border: 1px solid #fdf2d0;
  font-size: 14px;
  font-weight: bold;
  text-align: left;
  border-radius: 5px;
  padding: 15px;
}
</style>
