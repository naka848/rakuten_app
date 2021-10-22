<template>
  <div>
    <h2>第{{ item_rank }}位</h2>
    <img v-bind:src="item_img">
    <h3>{{ item_name }}</h3>
    <a href="item_url">商品の詳細をみる</a>
    <br>
    <a href="{{ item_url }}">商品の詳細をみる2</a>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    ItemObj: Object,
  },
  data(){
    return{
      item_rank: "",
      item_name: "",
      item_url: "",
    }
  },
  // DOM…WEBページとプログラミング言語を繋ぐ役割を持つ
  // 実行されるタイミング：DOMがまだ作られていないとき
  created(){
    console.log(this.ItemObj)
  },
  // 実行されるタイミング：DOMが作成された直後
  mounted(){
    const item = this.ItemObj.Item
    this.item_rank = item.rank
    this.item_name = item.itemName
    this.item_url = item.itemUrl
    this.item_img = item.mediumImageUrls[0].imageUrl
  },
};
</script>



    


