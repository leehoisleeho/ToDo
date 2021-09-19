<template>
  <v-touch @panup="onPandup">
    <div id="detailRightContainer">
      <h2 class="margin-l60 padding-l20">简介</h2>
      <div class="abstract">
        <p class="abstract-p word-style">
          {{ detailData.summary }}
        </p>
      </div>
      <h2 class="margin-l60 padding-l20">其它图书</h2>
      <div class="detail-list">
        <ul>
          <li @click="changeUrl(book)" v-for="book in otherMovies">
            <img :src="book.coverPath" alt="图书" />
          </li>
        </ul>
        <div v-if="showNoMoreData">暂无其它数据</div>
      </div>
    </div>
  </v-touch>
</template>

<script>
export default {};
</script>

<style>
</style>