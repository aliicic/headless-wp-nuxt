<template>
<main>
    <Header />
    <section class="section-01-00">
        <div class="tags-list">
            <ul>
                <li @click="updateTag(tag)" v-for="tag in tags" :key="tag.id" class="neobtn" :class="[tag.id === selectedTag ? activeClass : '']">
                    <a>{{ tag.name }}</a>
                    <!-- <span v-if="tag.id === selectedTag">✕</span> -->
                </li>
            </ul>
        </div>
        <div class="container">
            <div class="row">
                <div class="col-lg-4" v-for="post in sortedPosts" :key="post.id">
                    <nuxt-link :to="{ name : 'blog-slug' , params : { slug : post.slug } }" style="text-decoration:none">
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

    data: () => ({

        selectedTag: null,
        activeClass: "active"

    }),

    head() {
        return {
            title: 'مقالات'
        }
    },
    computed: {
        posts() {
            return this.$store.state.posts;
        },
        tags() {
            return this.$store.state.tags;
        },
        sortedPosts() {
            if (!this.selectedTag) return this.posts.filter(el => el.categories.includes(1));
            return this.posts.filter(el => el.categories.includes(1) && el.tags.includes(this.selectedTag));
        }
    },
    created() {
        this.$store.dispatch("getPosts");
        this.$store.dispatch("getTags");
    },
    methods: {
        updateTag(tag) {
          // if (!this.selectedTag) {
                this.selectedTag = tag.id;
        //     } else {
        //         this.selectedTag = null;
        //     }
         }
    }

}
</script>
