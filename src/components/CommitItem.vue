<template>
  <div>
    <div>{{truncate(sha)}}</div>
    <div>{{commit.author.name}}</div>
    <div>{{formatDate(commit.author.date)}}</div>
    <div>{{commit.message}}</div>
  </div>
</template>


<script>
import moment from "moment/moment";

export default {
  name: "CommitItem",
  props: ['commit', 'author', 'sha', 'html_url'],
  methods: {
    formatDate: function (date) {
      const outputFormat = "DD/MM/YYYY h:mm:ss A";
      return moment(date).format(outputFormat);
    },
    truncate: function (text) {
      return text.slice(0, 7)
    },
  }
}
</script>

<style scoped lang="scss">

</style>