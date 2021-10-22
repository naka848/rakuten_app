<template>
  <div>
    <h2>{{ book_title }}</h2>
    <!-- v-bind…タグの属性にVue3で用意した値を設定する -->
    <img v-bind:src="book_image" width="200">
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data:() => ({
    book_title: "",
    book_image: "",
  }),
  
  // async…awaitを含む関数につける
  async mounted(){
    const url = 'https://app.rakuten.co.jp/services/api/BooksBook/Search/20170404?format=json&title=%E5%A4%AA%E9%99%BD&booksGenreId=001004008&applicationId=1086601794285768274'
    // await…非同期に動かしたい処理につける
    const response = await fetch(url);
    const data = await response.json()
    console.log(data.Items[0])
    const first_item = data.Items[0].Item
    this.book_title = first_item.title
    this.book_image = first_item.smallImageUrl

  }
}
</script>


