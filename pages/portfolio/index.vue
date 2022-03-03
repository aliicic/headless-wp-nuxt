<template>
<main>
    <Header />
    <section class="section-01-00">
        <div class="container">
            <div class="row">
                <div class="col-lg-4" v-for="post in sortedPosts" :key="post.id">
                    <nuxt-link :to="{ name : 'blog-slug' , params : { slug : post.slug } }">
                        <div class="portfolio-item">
                            <div class="img-frame">
                                <img src="https://demo.themesberg.com/neumorphism-ui/assets/img/blog/blog-article-1.jpg" alt="">
                            </div>
                            <div class="content-frame">
                                <h4 class="title">
                                        {{post.title.rendered}}
                                </h4>
                                <span class="description">
                                    خلاصه موضوع اول
                                </span>
                                <a class="neobtn" href="">جزئیات</a>
                            </div>
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
            title: 'نمونه کار ها '
        }
    },
    computed: {
     posts() {
            return  this.$store.state.posts;
        },
     categories() {
            return  this.$store.state.categories;
        },
     sortedPosts() {

       return  this.posts.filter(el => el.categories.includes(23));

        }
    },


    created() {
        this.$store.dispatch("getPosts");
    },

}
</script>
