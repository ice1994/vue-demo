<template>
  <nav>
    <ul class="pagination justify-content-center">
      <li class="page-item" :class="{ 'disabled': !pages.has_pre }">
        <a class="page-link" href="#" @click.prevent="updatePage(pages.current_page - 1)">
          <span>&laquo;</span>
        </a>
      </li>
      <li class="page-item" v-for="page in pages.total_pages" :key="page" :class="{ 'active': pages.current_page === page }">
        <a class="page-link" href="#" @click.prevent="updatePage(page)">
          {{ page }}
        </a>
      </li>
      <li class="page-item" :class="{ 'disabled': !pages.has_next }">
        <a class="page-link" href="#" @click.prevent="updatePage(pages.current_page + 1)">
          <span>&raquo;</span>
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
  export default {
    props: ['pages'],
    methods: {
      updatePage(page) {
        this.$emit('emitPages', page)
      }
    }
  }
</script>
