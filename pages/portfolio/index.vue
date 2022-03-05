<template>
<main>
    <Header />
    <section class="section-01-00">
        <div class="container">
            <div class="row">
                <div class="col-lg-4" v-for="post in sortedPosts" :key="post.id">
                    <a :href="post.uagb_excerpt" target="_blank" rel="noreferrer" style="text-decoration:none">
                        <div class="portfolio-item">
                            <div class="img-frame">
                                <img :src="post.img" alt="">
                            </div>
                            <div class="content-frame">
                                <h6 class="title">
                                        {{post.title.rendered}}
                                </h6>
                                <span class="description">

                                </span>
                                <!-- <span class="date">{{ post.date}}</span> -->
                                <!-- <a class="neobtn" href="">جزئیات</a> -->
                            </div>
                        </div>
                    </a>
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

       return  this.posts.filter(el => el.categories.includes(2));

        }
    },


    created() {
        this.$store.dispatch("getPosts");

    },



}
</script>
