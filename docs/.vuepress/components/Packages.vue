<template>
  <div>
    <div v-if="loading">
      <p>Loading…</p>
    </div>

    <p v-if="rejected">
      Unable to get the packages list.
    </p>

    <ul v-if="success">
      <li
        v-for="pkg in packages"
        v-bind:key="pkg.package.ame">
        <a
          v-bind:href="'https://github.com/ovh/manager/tree/master/' + pkg.package.repository.directory"
          rel="noopener noreferrer"
          target="_blank">
          {{ pkg.package.name }}@{{ pkg.package.version }}
        </a>
        <br>
        <small>
          <strong>Description</strong>: {{ pkg.package.description ? pkg.package.description : 'n/a' }}
        </small>
        <hr>
      </li>
    </ul>
  </div>
</template>

<script>
const getWorkspace = (type) => {
  switch (type) {
    case 'components':
      return 'packages/components/*';
      break;
    case 'modules':
      return 'packages/manager/modules/*';
      break;
    case 'tools':
      return 'packages/manager/tools/*';
      break;
    default:
      return 'packages/manager/apps/*';
      break;
  }
};

export default {
  props: {
    type: String,
  },
  data() {
    return {
      loading: false,
      success: false,
      rejected: false,
      packages: [],
    };
  },
  async mounted () {
    this.loading = true;
    try {
      const packages = await fetch('/playground/assets/json/packages.json');
      const pacakgesAsJson = await packages.json();
      const { packagesList } = pacakgesAsJson.find((pkg) => pkg.workspace === getWorkspace(this.type));

      this.packages = packagesList;
      this.success = true;
    } catch (error) {
      this.rejected = true;
    } finally {
      this.loading = false;
    }
  }
}
</script>

<style lang="stylus" scoped>
  ul
    padding-left inherit

    li
      list-style-type none
</style>
