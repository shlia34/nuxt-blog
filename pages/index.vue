<template>
  <v-container class = "home">
    <div class="text">
      <v-col class = "greeting">{{greeting}}</v-col>
    <v-col class = "message">{{message}}</v-col>
    </div>
  </v-container>
</template>

<script>
import ContentfulAdapter from '../plugins/contentful.js'

export default {
  name: 'home',
  async asyncData () {
    const TopEntry = await ContentfulAdapter.getTop()

    return {
        greeting : TopEntry.fields.title,
        message : TopEntry.fields.description
    }
  }
}

</script>

<style>
.home {
  min-height: calc(100vh - 80px);
  text-align: center;
  position: relative;
}

.text {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  width: 80%;
  height: 50vh;
}

.greeting {
  font-size: 60px;
  font-weight: bold;
  color:#42B2C1;
}

.message {
  font-size: 20px;
}
</style>
