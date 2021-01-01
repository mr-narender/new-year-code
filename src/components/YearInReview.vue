<template>
  <div
    class="news news-image kenburns-bottom d-none d-md-block d-lg-block"
    :style="{ backgroundImage: 'url(' + news_urlToImage + ')' }"
  ></div>
  <div
    class="news news-headline d-none d-md-block d-lg-block"
    @click="openThisNews"
  >
    <span>{{ news_title }}</span>
  </div>
  <div
    class="news news-description d-none d-md-block d-lg-block"
    @click="openThisNews"
  >
    <span>{{ news_description }}</span>
  </div>
</template>

<script>
export default {
  name: "News",
  props: ["year", "apiKey"],
  data() {
    return {
      url:
        "http://newsapi.org/v2/everything?q=2020&sortBy=popularity&apiKey=" +
        this.apiKey,
      news_url: "",
      news_title: "",
      news_urlToImage: "",
      news_description: "",
    };
  },
  methods: {
    sleep: async function(ms) {
      return new Promise((resolve) => setTimeout(resolve, ms));
    },
    getNews: async function() {
      fetch(this.url)
        .then((response) => response.json())
        .then((newsData) => newsData.articles)
        .then(async (articles) => {
          for (let index = 0; index < articles.length; index++) {
            let article = articles[index];
            this.news_title = article.title;
            this.news_url = article.url;
            this.news_urlToImage = article.urlToImage;
            this.news_description = article.description;
            await this.sleep(3500);
          }
        });
    },
    openThisNews: function() {
      console.log("clicked");
      window.open(this.news_url, "_blank");
    },
  },
  mounted: function() {
    this.getNews();
    setInterval(() => {
      this.getNews();
    }, 6000);
  },
};
</script>

<style>
.news {
  position: fixed;
  height: 30vh;
  display: flex;
  align-items: center;
  justify-content: center;
  left: 0;
  right: 0;
}

.news-image {
  background-size: cover;
  margin: 10px 10px;
}

.news-headline {
  position: relative;
  height: initial;
  color: white;
  font-size: 2.5rem;
  cursor: pointer;
  top: 15rem;
}

.news-description {
  height: initial;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  top: 20rem;
}

.news-headline > span {
  background-color: crimson;
}

.news-description > span {
  background-color: white;
  color: crimson;
}

.kenburns-bottom {
  -webkit-animation: kenburns-bottom 10s ease-out alternate-reverse infinite;
  animation: kenburns-bottom 10s ease-out alternate-reverse infinite;
}

@-webkit-keyframes kenburns-bottom {
  0% {
    -webkit-transform: scale(1) translateY(0);
    transform: scale(1) translateY(0);
    -webkit-transform-origin: 50% 84%;
    transform-origin: 50% 84%;
  }
  100% {
    -webkit-transform: scale(1.25) translateY(15px);
    transform: scale(1.25) translateY(15px);
    -webkit-transform-origin: bottom;
    transform-origin: bottom;
  }
}
@keyframes kenburns-bottom {
  0% {
    -webkit-transform: scale(1) translateY(0);
    transform: scale(1) translateY(0);
    -webkit-transform-origin: 50% 84%;
    transform-origin: 50% 84%;
  }
  100% {
    -webkit-transform: scale(1.25) translateY(15px);
    transform: scale(1.25) translateY(15px);
    -webkit-transform-origin: bottom;
    transform-origin: bottom;
  }
}
</style>
