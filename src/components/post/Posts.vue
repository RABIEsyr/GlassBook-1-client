<template>
  <div>
    <div v-for="(post, index) in posts" :key="index" @click="inPostClick(post)">
      <my-post
        :image="'http://localhost:3000/static/' + post._id + '.PNG'"
        :text="post.text"
      >
      </my-post>
    </div>
  </div>
</template>

<script>
import Post from "./post";
import * as types from "../../store/types";
// import axios from "axios";
global.jQuery = require("jquery");
var $ = global.jQuery;
window.$ = $;

export default {
  data: () => ({
    index: 0,
    // posts: [],
  }),
    computed: {
      posts() {
        return this.$store.getters.getPosts;
      },
    },
  created() {
    // await this.$store.dispatch("getPostsHttp", 0).then(async() => {
    //  await this.$store.dispatch(types.GET_FRIEND_POSTS)
    //  });

     this.$store.dispatch(types.GET_FRIEND_POSTS)

    // axios
    //   .get("http://localhost:3000/post/friends-post", {
    //     headers: {
    //       authorization: localStorage.getItem("token"),
    //     },
    //   })
    //   .then((res) => {
    //     console.log("posts.vue aaa", res.data);
    //     this.posts = res.data;
    //   });
  },
  methods: {
    inPostClick(post) {
      console.log("Posts.vue", post);
    },
    //  scroll() {
    //   let t = this
    //   $(window).scroll(function() {
    //     if($(window).scrollTop() + $(window).height() == $(document).height()) {
    //        // console.log('App.vue scroll()', 'end')
    //         t.index += 3;
    //         console.log('Posts index end of page', t.index);
    //         t.$store.dispatch('getPostsHttp', t.index);
    //     }
    //   });
    //  },

    // worked
    // scroll() {
    //     let t =this
    //   $(window).scroll(function () {
    //     if (
    //       $(window).scrollTop() + $(window).height() >
    //       $(document).height() - 100
    //     ) {
    //       console.log("near bottom!");
    //       t.index += 3;
    //       t.$store.dispatch('getPostsHttp', t.index);
    //     }
    //   });
    // },

    scroll() {
      let t = this;
      $(window).scroll(function () {
        if (
          $(window).scrollTop() + $(window).height() >
          $(document).height() - 100
        ) {
          console.log(" bottom!");
          t.index += 3;
          t.$store.dispatch(types.GET_FRIEND_POSTS, t.index);
        }
      });
    },
  },
  mounted() {},
  components: {
    "my-post": Post,
  },
};
</script>

<style>
</style>
