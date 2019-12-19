<template>
  <div id="card">
    <div class="book-box">
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
                <span
                  class="itemchild-txt"
                  v-bind:class="itemchild.className"
                  v-html="itemchild.txt"
                ></span>
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
      book: "",
      action: ""
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
  top: 70px;
  width: 100%;
}
.book-box {
  text-align: center;
}
.book-img {
  width: 340px;
  height: auto;
}
.item-bg {
  width: 320px;
}
.item-content {
  position: relative;
  margin-bottom: 16px;
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
  height: 46px;
}
li {
  list-style-type: none;
  margin-left: 18px;
}
.itemchild-bg {
  width: 200px;
  height: 130px;
}
.itemchild-content {
  display: flex;
  overflow-x: scroll;
  margin-left: 100px;
  margin-right: 10px;
}
::-webkit-scrollbar {
  display: none;
}
.itemchild-item {
  display: flex;
  position: relative;
}
.itemchild-txt {
  position: absolute;
  text-align: center;
  display: inline-block;
  line-height: 18px;
  font-size: 16px;
  font-weight: 600;
}
.tc {
  top: 60px;
  width: 200px;
  height: 60px;
}
.sp1 {
  display: flex;
  align-items: center;
  justify-content: center;
}
.sp2 {
  top: 0;
  width: 200px;
  height: 130px;
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 20px;
}
.sp3 {
  display: flex;
  align-items: center;
  justify-content: center;
  line-height: 18px;
}

/* 以下是自适应样式 */

/** 平板及台式机 **/
@media only screen and (min-width: 540px) {
  .card-bg {
    width: 128px;
    margin-left: 20px;
  }
  #card {
    position: relative;
  }
  .bg-content {
    position: absolute;
    top: 70px;
    width: 100%;
  }

  .book-box {
    margin-left: 148px;
    text-align: left;
  }
  .book-img {
    width: 340px;
    height: auto;
  }
  .item-bg {
    width: 320px;
  }
  .item-content {
    position: relative;
    margin-bottom: 16px;
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
    height: 46px;
  }
  li {
    list-style-type: none;
    margin-left: 18px;
  }
  .itemchild-bg {
    width: 200px;
    height: 130px;
  }
  .itemchild-content {
    display: flex;
    overflow-x: scroll;
    margin-left: 100px;
    margin-right: 10px;
  }
  ::-webkit-scrollbar {
    display: none;
  }
  .itemchild-item {
    display: flex;
    position: relative;
  }
  .itemchild-txt {
    position: absolute;
    text-align: center;
    display: inline-block;
    line-height: 18px;
    font-size: 16px;
    font-weight: 600;
  }
  .tc {
    top: 60px;
    width: 200px;
    height: 60px;
  }
  .sp1 {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .sp2 {
    top: 0;
    width: 200px;
    height: 130px;
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 20px;
  }
  .sp3 {
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 18px;
  }
}
/** 手机 **/
@media only screen and (max-width: 540px) {
  .card-bg {
    width: 68px;
    margin-left: 10px;
    display: none;
  }
  #card {
    position: relative;
  }
  .bg-content {
    position: absolute;
    top: 60px;
    width: 100%;
  }

  .book-box {
    text-align: center;
  }
  .book-img {
    width: 260px;
    height: auto;
  }
  .item-bg {
    width: 260px;
  }
  .item-content {
    position: relative;
    margin-bottom: 30px;
  }
  .item-txt {
    position: absolute;
    top: 8px;
    font-size: 16px;
    font-weight: 600;
    text-align: center;
    width: 170px;
    padding-left: 80px;
    line-height: 16px;
  }
  .text-center {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 36px;
  }
  li {
    list-style-type: none;
    margin-left: -28px;
  }
  .itemchild-bg {
    width: 160px;
    height: 100px;
  }
  .itemchild-content {
    display: flex;
    overflow-x: scroll;
    margin-left: 0;
    margin-right: 10px;
  }
  ::-webkit-scrollbar {
    display: none;
  }
  .itemchild-item {
    display: flex;
    position: relative;
  }
  .itemchild-txt {
    position: absolute;
    text-align: center;
    display: inline-block;
    line-height: 16px;
    font-size: 13px;
    font-weight: 600;
  }
  .tc {
    top: 50px;
    width: 160px;
    height: 40px;
  }
  .sp1 {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .sp2 {
    top: 0;
    width: 160px;
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 16px;
  }
  .sp3 {
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 15px;
  }
}
</style>
