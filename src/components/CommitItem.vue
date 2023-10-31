<template>
  <div class="mt-3">
    <div class="flex gap-x-2">
      <div class="text-green-600 font-medium">
        <a :href="html_url" target="_blank">{{truncate(sha)}}</a>
      </div>
      <div> By
        <a :href="author.html_url" target="_blank"
           class="text-green-600 font-bold hover:text-green-900">
        {{commit.author.name}}</a>
      </div>
      <div> at <span class="font-bold text-sm">{{formatDate(commit.author.date)}}</span></div>
    </div>
    <div>{{commit.message}}</div>
  </div>
</template>


<script>
import moment from "moment/moment";
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";


export default {
  name: "CommitItem",
  components: {FontAwesomeIcon},
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