<template>
<main>
    <Header />
    <section class="section-00-00">
        <div class="container">
            <div class="row">
                <div class="col-lg-6">
                    <div class="content">
                        <h1>نبولار</h1>
                        <h2>طراح و توسعه دهنده وب</h2>
                        <p>

                        </p>

                    </div>
                </div>
                <div class="col-lg-6">
                    <div class="img-frame">
                        <img src="~/assets/imgs/pic.jpg" alt="" />
                    </div>
                </div>
            </div>
        </div>
    </section>
    <section class="section-00-01">
        <div class="container">
            <div class="row skill-frame justify-content-center">
                <div class="col-lg-4 skill-items">
                    <div class="card-item">
                        <div class="icon-frame" style="background:#ff7058;">
                            <img src="~/assets/imgs/design.png" alt="">
                        </div>
                        <h4 class="text-center my-2">
                            طراحی سایت
                        </h4>
                        <p class="text-center">
                            طراحی انواع وب سایت های شخصی، شرکتی، فروشگاهی و خبری همراه با آموزش و پشتیبانی
                        </p>
                    </div>
                </div>
                <div class="col-lg-4 skill-items">
                    <div class="card-item">
                        <div class="icon-frame" style="background:#ffd05b">
                            <img src="~/assets/imgs/develop.png" alt="">
                        </div>
                        <h4 class="text-center my-2">
                            وب اپلیکیشن
                        </h4>
                        <p class="text-center">
                            طراحی و توسعه وب اپلیکیشن با طراحی و کاربرد های اختصاصی
                        </p>
                    </div>
                </div>
                <div class="col-lg-4 skill-items">
                    <div class="card-item">
                        <div class="icon-frame" style="background: #90dfaa;">
                            <img src="~/assets/imgs/support.png" alt="">
                        </div>
                        <h4 class="text-center my-2">
                            پشتیبانی
                        </h4>
                        <p class="text-center">
                            تعمیر وبسایت هایی که کارکرد آنها مختل شده است ، بروزرسانی و رفع ایراد ها
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <section class="section-00-02">
        <div class="container">
                <h4 class="title">تماس با ما</h4>
                <p class="text-center mb-5">اگر نیاز به مشاوره فرم رو زیر رو تکمیل و ارسال کنید ، ما با شما تماس میگیریم</p>

            <form class="row g-3" @submit.prevent="">

                <div class="col-md-6">
                    <label for="inputEmail4" class="form-label">نام</label>
                    <input type="text" v-model="contactForm['text-name']" class="form-control" id="inputEmail4">
                </div>
                <div class="col-md-6">
                    <label for="inputPassword4" class="form-label">شماره تماس</label>
                    <input type="tel" v-model="contactForm['tel-name']" class="form-control" id="inputPassword4">
                </div>
                <div class="col-6">
                    <label for="inputAddress" class="form-label">ایمیل</label>
                    <input type="email" v-model="contactForm['email-address']" class="form-control" id="inputAddress" placeholder="1234 Main St">
                </div>
                <div class="col-6">
                    <label for="inputAddress2" class="form-label">موضوع</label>
                    <input type="text" v-model="contactForm['text-subject']" class="form-control" id="inputAddress2" placeholder="">
                </div>
                <div class="col-12">
                    <label for="exampleFormControlTextarea1" class="form-label">موارد بیشتر ؟</label>
                    <textarea class="form-control" v-model="contactForm['textarea-778']" id="exampleFormControlTextarea1" rows="6" style="height: unset;"></textarea>
                </div>
                <div class="col-12">
                    <button  @click.prevent="sendEmail()" class="neobtn mx-auto">
                        <span v-if="loading" class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span>
                      ارسال
                    </button>
                </div>
            </form>
             <p v-if="message"> {{ message }} </p>
        </div>
    </section>
    <section class="section-00-03">
        <div class="container">
            <h4 class="title">وبلاگ</h4>
            <p class="text-center mb-5">سعی میکنیم در این قسمت محتوای باکیفیت در زمینه طرحی و توسعه وب قرار دهیم</p>
            <div class="row mb-3">
               <div class="col-lg-4" v-for="post in posts" :key="post.id">
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
            <nuxtLink to="/blog" class="neobtn mx-auto ">همه موارد</nuxtLink>

        </div>
    </section>
    <section class="section-00-04">
        <div class="container">
            <div class="row">
                <div class="col-lg-4">
                    <div class="user-item card">
                        <div class="profile-img">
                            <img src="~/assets/imgs/ali-aghakhani.jpg" alt="">
                        </div>
                        <div class="card-content">
                            <h5>علی آقاخانی</h5>
                            <p>طراح و توسعه دهنده وب</p>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/js.png" alt="">
                            </div>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/vue.png" alt="">
                            </div>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/nxt.png" alt="">
                            </div>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/wp.png" alt="">
                            </div>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/gsap.png" alt="">
                            </div>
                            <div class="icon-frame">
                                <img src="~/assets/imgs/sass.png" alt="">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <Footer />
</main>
</template>

<script>

export default {
    name: 'IndexPage',

    data: () => ({

        contactForm: {
            'text-name': '',
            'tel-name': '',
            'email-address': '',
            'text-subject': '',
            'textarea-778': '',
        },
        message : '',
        loading : false

    }),

    head() {
        return {
            title: 'صفحه اصلی'
        }
    },
    computed: {
        posts() {
            return this.$store.state.posts.slice(0,3);
        },
        tags() {
            return this.$store.state.tags;
        },
        // sortedPosts() {
        //   if (!this.selectedTag) return this.posts;
        //   return this.posts.filter(el => el.tags.includes(this.selectedTag));
        // }
    },
    methods: {

       async sendEmail() {
       this.loading = true
          try{

            const { message }  =  await  this.$axios.$post('https://cmsnuxt.nebular.ir/wp-json/contact-form-7/v1/contact-forms/5/feedback', this.contactForm,

                {
                    headers: {
                        "content-type": "multipart/form-data",

                    },
                })

            this.message = message
            this.loading = false
          }catch(e){

            this.message = e
            this.loading = false

          }



        }

    },
    created() {
          this.$store.dispatch("getPosts");
        // this.$store.dispatch("getCats");
    },

}
</script>
