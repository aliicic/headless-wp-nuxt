<template>
<main>
    <Header />
    <section class="section-02-00">
        <div class="container">
            <div class="row">
                <div class="col-12">

                    <span class="date">{{ post.date }}</span>
                    <span class="author">{{post.display_name}}</span>
                    <h4 class="title text-end">
                        {{ post.title.rendered }}
                    </h4>
                    <div class="description" v-html="post.content.rendered"></div>

                </div>
            </div>
        </div>
    </section>
    <Footer />
</main>
</template>

<script>
export default {
    computed: {
        posts() {
            return this.$store.state.posts;
        },
        post() {
            return this.posts.find(el => el.slug === this.slug);
        }
    },
    data() {
        return {
            slug: this.$route.params.slug
        };
    },
    created() {
        this.$store.dispatch("getPosts");
    }
};
</script>
