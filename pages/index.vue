<template>
 <div>
  <Frame/>
  <Tutorial/>
 </div>
</template>

<script>
export default {
  name: 'IndexPage',

  head() {
    return {
      title : 'مقالات'
    }
  },
  computed: {
     posts() {
      return  this.$store.state.posts;
    },
    tags() {
      return this.$store.state.tags;
    },
    // sortedPosts() {
    //   if (!this.selectedTag) return this.posts;
    //   return this.posts.filter(el => el.tags.includes(this.selectedTag));
    // }
  },
  created() {
    this.$store.dispatch("getCats");
  },

}
</script>
