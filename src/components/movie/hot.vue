<template>
  <div class="hot">
    <div class="movie">
      <ul class="movie-list">
        <li class="movie-item" v-for="hotItem in movieHot.hot">
          <movie-item :movieInfo="hotItem"></movie-item>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import movieItem from 'components/movie/movieItem'
export default {
  data() {
    return {
      movieHot: {}
      // isLoaded: false
    }
  },
  created() {
    this.axios.get('/movie/movieHot').then(response => {
      if (response.statusText === 'OK') {
        this.movieHot = response.data.data.data
        // console.log(this.movieHot)
      }
    }).catch(error => {
      console.log(error)
    })
    /* let url = `/movie/list.json?type=hot&offset=0&limit=1000`
    http://m.maoyan.com/movie/list.json?type=hot&offset=0&limit=1000
    this.axios.get(url).then(response => {
      if (response.statusText === 'OK') {
        this.movieHot = response.data.data.movies
        setTimeout(() => {
          this.isLoaded = true
        }, 1000);
        console.log(this.movieHot)
      }
    }).catch(error => {
      console.log(error)
    }) */
  },
  components: {
    'movie-item': movieItem
  }
}
</script>

<style lang="less" scoped>
.hot {
  width: 100%;
  overflow: hidden;
  .movie {
    width: 100%;
    .movie-item {
      width: 100%;
      border-bottom: 1px solid #eee;
    }
  }
}
</style>
