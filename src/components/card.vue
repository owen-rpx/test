<template>
  <div id="card">
    <div>
      <img class="book-img" v-bind:src="book" alt />
    </div>
    <img class="card-bg" v-bind:src="action" alt />

    <div class="bg-content">
      <ul>
        <li v-for="item in items">
          <div class="item-content">
            <img class="item-bg" v-bind:src="item.img" />
            <div class="item-txt" v-bind:class="{ 'text-center': !item.text02 }">
              <div>{{ item.text01 }}</div>
              <div v-if="item.text02">{{ item.text02 }}</div>
            </div>
            <div class="itemchild-content">
              <div class="itemchild-item" v-for="itemchild in item.child">
                <img class="itemchild-bg" v-bind:src="itemchild.image" />
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "card",
  data() {
    return {
	  items: [],
	  book:'',
	  action: ''
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      axios.get("/static/data.json").then(
        response => {
		  this.items = response.data.itemdata;
		  this.book = response.data.book;
		  this.action = response.data.action;
        },
        response => {
          console.log("error");
        }
      );
    }
  }
};
</script>

<style scoped>
.card-bg {
  width: 128px;
  margin-left: 20px;
}
#card {
  position: relative;
}
.bg-content {
  position: absolute;
  top: 60px;
  width: 100%;
}
.book-img {
  width: 340px;
  height: auto;
  margin-left: 160px;
}
.item-bg {
  width: 320px;
}
.item-content {
  position: relative;
  margin-bottom: 30px;
}
.item-txt {
  position: absolute;
  top: 8px;
  font-size: 18px;
  font-weight: 600;
  text-align: center;
  width: 250px;
  padding-left: 80px;
  line-height: 22px;
}
.text-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 55px;
}
li {
  list-style-type: none;
  margin-left: 18px;
}
.itemchild-bg {
  width: 160px;
}
.itemchild-content {
  display: flex;
  overflow: scroll;
  margin-left: 100px;
  margin-right: 10px;
}
.itemchild-item {
  margin: 0 2px;
}
</style>
