<script>
import { defineComponent, ref } from "vue";
import spinner from "./spinner.vue";
import viewArticle from "./viewArticle.vue";
export default defineComponent({
  props: {
    PaperUrl: String,
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
        method: "get", // *GET, POST, PUT, DELETE, etc.
        mode: "cors", // no-cors, *cors, same-origin
        headers: {
          "Content-Type": "application/json",
        },
        //body: JSON.stringify(datare) // body data type must match "Content-Type" header
      }).catch((err) => alert(err));
      // console.log(await response.json())
      this.isLoading = false;
      return await response.json().then((res) => (this.PaperFile = res));
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
    handleOk (e) {
      
     return this.isVisible = false;
    }
  },
});
</script>

<template>
   <div>
    <a-modal  width="80%" v-model:visible="isVisible" :title="nModalTitle" @ok="handleOk">
      <p v-html="nModalTitle"></p>
      <p v-html="nModalText"></p>
      
    </a-modal>
  </div>
  <div style="margin: 10px auto; padding: 20px">
    {{ PaperUrl }}
    <div>{{ isDataExist }}</div>

    <a-spin size="large" :spinning="isLoading">
      <div
        @click="postInfo(mi)"
        v-for="(mi, index) in PaperFile"
        :key="index"
        style="
          background-color: grey;
          color: #fff;
          width: 80%;
          margin: 10px auto;
          padding: 20px;
        "
      >
        <h2 v-html="mi.title.rendered"></h2>
        <div v-html="mi.excerpt.rendered"></div>
        <!-- <viewArticle :title="mi.title.rendered" :article="mi.excerpt.rendered" v-model:showModal="nModal" /> -->
      </div>
    </a-spin>

    <h1>Component Work!</h1>
    <!-- <p>{{ newsPost }}</p> -->
    <a-button @click="getPapers()">primary</a-button>
  </div>
</template>
