<template>
  <div class="container-fluid">
    <div>Latest Commits</div>
    <div>
      <template v-for="{ html_url, sha, author, commit } in commits" :key="html_url" >
        <CommitItem
            :commit="commit"
            :author="author"
            :sha="sha"
            :html_url="html_url" />
      </template>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import CommitItem from "./CommitItem.vue";
export default {
  //name: 'component-name',
  //parent: '',
  components: {CommitItem},
  directives: {},
  filters: {},
  mixins: [],
  props: {},
  data: function () {
    return {
      API_URL:
        "https://api.github.com/repos/vuejs/core/commits?per_page=10&sha=main",
      commits: null,
    };
  },
  computed: {},
  watch: {},
  beforeCreate: function () {},
  created: function () {
    this.fetchData();
  },
  beforeMount: function () {},
  mounted: function () {},
  beforeUpdate: function () {},
  updated: function () {},
  activated: function () {},
  deactivated: function () {},
  beforeDestroy: function () {},
  destroyed: function () {},
  methods: {
    fetchData: async function () {
      this.commits = await (await fetch(this.API_URL)).json();
      console.log(this.commits)
    },

  },
};
</script>

<style lang="scss" scoped></style>
