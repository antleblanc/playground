<template>
  <div>
    <div v-html="content"></div>
  </div>
</template>

<script>
import md from 'markdown-it';

export default {
  data() {
    return {
      content: null
    };
  },
  async mounted () {
    try {
      const contributing = await fetch('https://raw.githubusercontent.com/ovh/manager/master/CONTRIBUTING.md');
      const text = await contributing.text();

      this.content = md().render(text);
    } catch (error) {
      console.log('error', error);
    } finally {
    }
  }
}
</script>
