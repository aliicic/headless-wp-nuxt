<template>
    <main>
      <Header />
        <section class="section-01-00">
            <div class="container">
                <div class="row">
                    <div class="col-lg-4" v-for="post in sortedPosts" :key="post.id">
                     <nuxt-link :to="{ name : 'blog-slug' , params : { slug : post.slug } }">
                        <div class="blog-item p-4">
                            <span class="date">{{ post.date}}</span>
                            <h4 class="title">
                                {{post.title.rendered}}
                            </h4>
                            <!-- <span class="description">
                                خلاصه موضوع اول
                            </span> -->
                            <span class="author">
                               {{post.display_name}}
                               نام نویسنده
                            </span>
                        </div>
                      </nuxt-link>
                    </div>

                </div>
            </div>
        </section>
       <Footer />
    </main>
</template>

<script>
export default {

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
    sortedPosts() {
     // if (!this.selectedTag) return this.posts;
      return this.posts.filter(el => el.categories.includes(1));
    }
  },
  created() {
    this.$store.dispatch("getPosts");
  },

}
</script>
