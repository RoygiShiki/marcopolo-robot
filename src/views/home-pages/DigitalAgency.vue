<template>
    <Layout header-class="header-left-align" nav-alignment="left" :header-transparency="true" :show-top-header="false" buy-button-class="btn-default btn-small">
        <!-- Start Slider Area -->
        <div class="slider-area slider-style-4 slider-dot rn-slick-dot rn-slick-arrow">
            <VueSlickCarousel v-bind="sliderSetting" :autoplay="true" :pauseOnHover="false" :autoplaySpeed="5000">
                <div v-for="(slider, index) in sliderData" :key="index" class="single-slide">
                    <div class="height-950 bg-overlay bg_image"
                         :style="{'background-image': `url(${require(`@/assets/images/bg/${slider.image}.jpg`)})`}">
                        <div class="container">
                            <div class="row row--30 align-items-center">
                                <div class="order-2 order-lg-1 col-lg-7">
                                    <div class="inner text-start">
                                        <h1 class="title" v-html="slider.title"/>
                                        <p class="description" v-html="slider.description"/>
                                        <div class="button-group mt--30">
                                            <a class="btn-default"
                                               :href="slider.site"
											   target="_blank">
                                                Official Website
                                            </a>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </VueSlickCarousel>
        </div>
        <!-- End Slider Area -->

        <!-- Start Service Area -->
        <div class="rn-service-area rn-section-gap">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <SectionTitle
                            text-align="center"
                            subtitle="About Jaten."
                            title="Products provide for you."
                            description="Jaten is a world-leading provider of AGV robots and intelligent logistics systems. It was established in 2002. So far, more than 60 Fortune 500 companies have used Jaten's products. Jaten products are widely used in various industries such as automobile, electronics, lithium battery production, chemical industry, daily necessities and heavy machinery and equipment production."
                            data-aos="fade-up"
                        />
                    </div>
                </div>
                <ServiceFive
                    service-style="gallery-style"
                    text-align="left"
                />
            </div>
        </div>
        <!-- End Service Area -->

        <Separator/>
		
		<!-- Start Progressbar Area -->
		<div class="rwt-progressbar-area rn-section-gap">
		    <div class="container">
		        <div class="row mb--25">
		            <div class="col-lg-10 offset-lg-1">
		                <SectionTitle
		                    text-align="center"
		                    subtitle="Our Partners"
		                    title="Company Partners"
		                    description="We have lots of partners all around the world."
		                    data-aos="fade-up"
		                />
		            </div>
		        </div>
		        <div class="row">
		            <div class="col-lg-10 offset-lg-1">
		                <Progressbar
		                    :progress-data="progressCircleData"
		                    :progress-style="5"
		                    column="col-lg-6 col-md-6 col-sm-6 mt--30 col-12"
		                />
		            </div>
		        </div>
		    </div>
		</div>
		<!-- Start Progressbar Area -->
		
		<Separator/>

        <!-- Start Portfolio Area -->
        <div class="rwt-portfolio-area rn-section-gap">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <SectionTitle
                            text-align="center"
                            subtitle="Products"
                            title="Products"
                            description="Jaten products are widely used in various industries such as automobile, electronics, lithium battery production, chemical industry, daily necessities and heavy machinery and equipment production."
                            data-aos="fade-up"
                        />
                    </div>
                </div>
                <Portfolio :portfolio-data="portfolioData"/>
            </div>
        </div>
        <!-- End Portfolio Area -->

        <Separator/>

        <!-- Start Testimonial Area  -->
      <!--  <div class="rwt-testimonial-area rn-section-gap">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <SectionTitle
                            text-align="center"
                            subtitle="Client Feedback"
                            title="What People Are Saying"
                            description="There are many variations of passages of Lorem Ipsum available, <br /> but the majority have suffered alteration"
                            data-aos="fade-up"
                        />
                    </div>
                </div>
                <div class="row row--15">
                    <div class="col-lg-4 col-md-6 col-12"
                         v-for="(testimonial, index) in testimonialData"
                         :key="index">
                        <Testimonial :testimonial="testimonial" :testimonial-style="2"/>
                    </div>
                </div>
            </div>
        </div> -->
        <!-- End Testimonial Area  -->

        <Separator/>

        <!-- Start Blog Area -->
        <div class="blog-area rn-section-gap">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <SectionTitle
                            text-align="center"
                            subtitle="Get The Latest News"
                            title="What Our Trending News"
                            description="We provide company and finance service for <br /> startups and company business"
                            data-aos="fade-up"
                        />
                    </div>
                </div>
                <div class="row row--15">
                    <div class="col-lg-4 col-md-6 col-sm-12 col-12 mt--30"
                         data-aos="slide-up"
                         data-aos-duration="800"
                         :data-aos-delay="100 + index"
                         v-for="(blog, index) in posts"
                         :key="index"
                         v-if="index < 3">
                        <BlogPost :blog="blog"/>
                    </div>
                </div>
            </div>
        </div>
        <!-- End Blog Area -->
    </Layout>
</template>

<script>
    import Layout from '../../components/common/Layout'
    import SectionTitle from '../../components/elements/sectionTitle/SectionTitle'
    import Separator from '../../components/elements/separator/Separator'
    import VueSlickCarousel from 'vue-slick-carousel'
    import BlogPost from '../../components/blog/BlogPost'
    import BlogPostMixin from '../../mixins/BlogPostMixin'
    import Testimonial from '../../components/elements/testimonial/Testimonial'
    import Portfolio from '../../components/elements/portfolio/Portfolio'
    import ServiceFive from '../../components/elements/service/ServiceFive'
    import Progressbar from '../../components/elements/progressbar/Progressbar'

    export default {
        name: 'DigitalAgency',
        components: {
            Progressbar,
            ServiceFive,
            Portfolio,
            Testimonial,
            BlogPost,
            Separator,
            SectionTitle,
            Layout,
            VueSlickCarousel
        },
        mixins: [BlogPostMixin],
        data() {
            return {
                sliderSetting: {
                    infinite: true,
                    slidesToShow: 1,
                    slidesToScroll: 1,
                    dots: true,
                    arrows: true,
                    responsive: [
                        {
                            breakpoint: 800,
                            settings: {
                                slidesToShow: 1,
                            }
                        },
                        {
                            breakpoint: 993,
                            settings: {
                                slidesToShow: 1,
                            }
                        },
                        {
                            breakpoint: 580,
                            settings: {
                                slidesToShow: 1,
                            }
                        },
                        {
                            breakpoint: 481,
                            settings: {
                                slidesToShow: 1,
                            }
                        }
                    ]
                },
                sliderData: [
                    {
                        // image: 'bg-image-6',
                        image: 'jiateng',
                        title: 'Jaten',
                        description: 'AGV/AMR vendor keen on customized solution since 2005.',
						site: 'https://www.jtrobots.com/index/index/index'
                    },
                    {
                        // image: 'bg-image-14',
                        image: 'robosense',
                        title: 'Creative Agency.',
                        description: 'We help our clients succeed by creating brand identities, digital experiences, and print materials.',
						site: 'https://www.robosense.ai/en'
                    },
                    {
                        // image: 'bg-image-15',
                        image: 'robotics',
                        title: 'Startup Agency.',
                        description: 'We help our clients succeed by creating brand identities, digital experiences, and print materials.',
						site: 'https://en.dh-robotics.com/'
                    },
                ],
                testimonialData: [
                    {
                        image: 'testimonial-01',
                        name: 'Sr Janen Sara',
                        designation: 'Sr Product Designer',
                        location: 'CO Miego, AD, USA',
                        description: '???Proin libero vel lorem dui lupus est aliquet luctus purus justo eget libero sed lorem.???',
                    },
                    {
                        image: 'testimonial-02',
                        name: 'Afsana Nila',
                        designation: 'App Developer',
                        location: 'Bangladesh',
                        description: '???Proin libero vel lorem dui lupus est aliquet luctus purus justo eget libero sed lorem.???',
                    },
                    {
                        image: 'testimonial-03',
                        name: 'Afanan Sifa',
                        designation: 'Accounts Manager',
                        location: 'Poland',
                        description: '???Proin libero vel lorem dui lupus est aliquet luctus purus justo eget libero sed lorem.???',
                    },
                ],
                progressCircleData: [
                    {
                        id: 1,
                        title: 'Partners From China',
                        percentage: 85,
                        subtitle: 'We have cooperative relations with 85% of enterprises in China.',
                        strokeColor: '#0f0f11',
                        strokePath: '#059DFF'
                    },
                    {
                        id: 2,
                        title: 'Partners From Whole World',
                        percentage: 60,
                        subtitle: 'We have cooperative relations with 60% of enterprises in the world.',
                        strokeColor: '#0f0f11',
                        strokePath: '#059DFF'
                    }
                ],
                portfolioData:  [
                    {
                        id: 1,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                        title: 'App Development',
                        subtitle: 'Branded client',
                        date: '30 May 2021',
                        client: 'Rainbow Themes',
                        category: 'AGV',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-03.jpg`)
                        }
                    },
                    {
                        id: 2,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                        title: 'Business Development',
                        subtitle: 'Awesome portfolio',
                        date: '01 March 2021',
                        client: 'Rainbow Themes',
                        category: 'Tractor',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-03.jpg`)
                        }
                    },
                    {
                        id: 3,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-03.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-03.jpg`),
                        title: 'Photoshop Design',
                        subtitle: 'Awesome portfolio',
                        date: '01 March 2021',
                        client: 'Rainbow Themes',
                        category: 'AutoForklift',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-03.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-03.jpg`)
                        }
                    },
                    {
                        id: 4,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-04.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-04.jpg`),
                        title: 'Native Application',
                        subtitle: 'Awesome portfolio',
                        date: '01 March 2021',
                        client: 'Rainbow Themes',
                        category: 'AGV',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-04.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-04.jpg`)
                        }
                    },
                    {
                        id: 5,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-05.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-05.jpg`),
                        title: 'Vue Development',
                        subtitle: 'Awesome portfolio',
                        date: '01 March 2021',
                        client: 'Rainbow Themes',
                        category: 'Tractor',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-05.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-03.jpg`)
                        }
                    },
                    {
                        id: 6,
                        portfolioImage: require(`@/assets/images/portfolio/portfolio-06.jpg`),
                        image: require(`@/assets/images/portfolio/portfolio-06.jpg`),
                        title: 'App Installment',
                        subtitle: 'Awesome portfolio',
                        date: '01 March 2021',
                        client: 'Rainbow Themes',
                        category: 'Tractor',
                        awards: ['2020 Design beautiful apps Finale Awards'],
                        excerpt: 'Design beautiful apps.',
                        body: `<p>In a typical Vue application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme).</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p> <br /> <p>that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.</p>`,
                        btn: {
                            buttonText: 'View Projects',
                            link: '/'
                        },
                        largeImage: require(`@/assets/images/portfolio/portfolio-06.jpg`),
                        subContent: {
                            title: 'Digital Marketing.',
                            subtext: 'We provide digital experience services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent2: {
                            title: 'App Development.',
                            subtext: 'We provide App Development services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        subContent3: {
                            title: 'Solution.',
                            subtext: 'We provide problem solutions services to startups and small businesses. We help our clients succeed by creating brand identities.'
                        },
                        gallery: {
                            imageOne: require(`@/assets/images/portfolio/portfolio-01.jpg`),
                            imageTwo: require(`@/assets/images/portfolio/portfolio-02.jpg`),
                            imageThree: require(`@/assets/images/portfolio/portfolio-06.jpg`)
                        }
                    }
                ]
            }
        }
    }
</script>