<template>
  <router-link
    class="flex flex-col m-auto w-full md:w-3/5 lg:w-2/5 mb-4"
    :to="`/${slug}`"
  >
    <h3 class="flex text-md font-semibold text-gray-700">{{ title }}</h3>
    <p class="flex leading-relaxed">{{ description | ellipsis }}</p>
    <div class="flex flex-row flex-wrap mt-4">
      <a
        v-for="tag in tags"
        :key="tag"
        class="flex text-xs font-semibold px-2 py-1 mr-2 rounded border border-blue-500 text-blue-500"
      >
        #{{ tag }}
      </a>
    </div>
  </router-link>
</template>
<script>
export default {
  props: {
    slug: {
      type: String
    },
    title: {
      type: String
    },
    description: {
      type: String
    },
    tags: {
      type: Array,
      default: () => []
    }
  },
  filters: {
    ellipsis(value) {
      return value && value.length > 50
        ? `${value.slice(0, 50)}...`
        : value
    }
  }
}
</script>
