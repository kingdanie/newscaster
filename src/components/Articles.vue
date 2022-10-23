<template>
  <div>
    <a-modal
      width="80%"
      wrap-class-name="news-modal"
      centered
      v-model:visible="isVisible"
      :title="nModalTitle"
      @ok="handleOk"
      footer=""
    >
      <p v-html="nModalTitle"></p>
      <p v-html="nModalText"></p>
    </a-modal>
  </div>
  <div style="margin: 10px auto">
    <!-- {{ PaperUrl }} -->
    <h1 class="page-title">{{ pageTitle }}</h1>
    <a-spin size="large" :spinning="isLoading">
      <div class="grid-s">
        <div
          @click="postInfo(mi)"
          v-for="(mi, index) in PaperFile"
          :key="index"
          style="
            background-color: #001529;
            color: #fff;
            border-radius: 5px;
            padding: 20px;
            cursor: pointer;
          "
        >
          <h2 class="article-title" v-html="mi.title.rendered"></h2>
          <div v-html="mi.excerpt.rendered"></div>
          <!-- <viewArticle :title="mi.title.rendered" :article="mi.excerpt.rendered" v-model:showModal="nModal" /> -->
        </div>
      </div>
    </a-spin>
    <ErrorAlert  v-if="isError"/>
    <!-- <h1>Component Work!</h1> -->
    <!-- <a-button @click="getPapers()">primary</a-button> -->
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import spinner from "./spinner.vue";
import viewArticle from "./ViewArticle.vue";
import PageTitle from "./PageTitle.vue";
import ErrorAlert from '@/components/ErrorAlert.vue'
export default defineComponent({
  components: { PageTitle, ErrorAlert },
  props: {
    PaperUrl: String,
    pageTitle: String,
  },
  data() {
    return {
      PaperUrl: this.PaperUrl,
      PaperFile: [],
      isLoading: true,
      nModal: false,
      nModalText: "",
      nModalTitle: "",
      isVisible: false,
      isError: false,
    };
  },
  mounted() {
    // this.newsPost;
    // this.getPapers();
  },
  created() {
    this.getPapers();
  },
  computed: {
    getPaper() {
      if (this.PaperFile.length === 0) {
        console.log("Data Changed");
        //return this.PaperFile.push(this.getPapers())
      }
    },
    isDataExist() {
      // `this` points to the component instance
      return this.PaperFile.length > 0 ? "Yes" : "No";
    },
  },
  methods: {
    async getPapers() {
      console.log("Event Fired");
      const getUrl = this.PaperUrl + "/wp-json/wp/v2/posts?per_page=30";
      //console.log(getUrl)
      const response = await fetch(getUrl, {
        method: "get",
        mode: "cors",
        headers: {
          "Content-Type": "application/json",
        },
        //body: JSON.stringify(datare) // body data type must match "Content-Type" header
      }).catch(
        (err) => (this.isError = true)  && console.log(err)
        );
      // console.log(await response.json())
      this.isLoading = false;
      return await response.json().then((res) => (this.PaperFile = res))
    },
    pickaboo() {
      console.log(this.PaperUrl);
      alert("I see you");
    },
    postInfo(ob) {
      console.log(ob);
      this.nModalTitle = ob.title.rendered;
      this.nModalText = ob.content.rendered;
      this.isVisible = true;
      return (this.nModal = !this.nModal);
    },
    handleOk(e) {
      return (this.isVisible = false);
    },
  },
  components: { PageTitle, ErrorAlert },
});
</script>

<style>
.grid-s {
  display: grid;
  grid-template-columns: 1fr;
  gap: 10px;
}

@media screen and (min-width: 768px) {
  .grid-s {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 1020px) {
  .grid-s {
    grid-template-columns: repeat(4, 1fr);
  }
}
body {
  display: flex;
  place-items: center;
}

.news-modal {
  background-color: #00152994;
}
.news-modal .ant-modal-body {
  overflow-y: scroll;
  max-height: 70vh;
}
.news-modal ant-modal-close {
  color: red;
}

.news-modal .ant-modal-title {
  color: #001529;
  font-size: 2.5em;
  line-height: 1;
}

.ant-modal-body {
  font-size: 16px;
  color: rgb(15, 15, 15);
  font-weight: 500;
}
.ant-modal-close {
  color: red;
}

.ant-modal-body .ant-btn-primary {
  border-color: #001529;
  background: #001529;
}
.page-title {
  font-size: 4rem;
  font-weight: 800;
  color: #001529;
}

.article-title {
  font-size: 2.5em;
  color: #b6d3eebe;
}

@media screen and (max-width: 600px) {
  .page-title{
    font-size: 2rem;
  }
}
</style>
