<template>
  <!-- v-for="変数 in 配列" -->
  <div>
    <h1>楽天商品ランキング（20代）</h1>
    <HelloWorld
      v-for="shohin in shohinList"
      v-bind:ItemObj="shohin"
      v-bind:key="shohin.Item.rank"
    />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      // 配列の初期化は[]
      // 文字列の初期化は""
      shohinList: [],
    };
  },

  // async…awaitを含む関数につける
  async mounted() {
    const url =
      "https://app.rakuten.co.jp/services/api/IchibaItem/Ranking/20170628?format=json&age=20&applicationId=1086601794285768274";
    // await…非同期に動かしたい処理につける
    // fetch…非同期関数
    const response = await fetch(url);
    const data = await response.json();
    //ここを変えましたー。dataの中にItemsというキーに対して配列が値で入っている
    this.shohinList = data.Items;
    // console.log(data);
    // console.log(this.shohinList);
  },
};
</script>


