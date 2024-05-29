<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid">
      <a
        class="navbar-brand"
        href="#"
        >Navbar</a
      >
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div
        class="collapse navbar-collapse"
        id="navbarSupportedContent"
      >
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <navbar-link
            v-for="(page, index) in publishedPages"
            class="nav-item"
            :key="index"
            :index="index"
            :page="page"
          >
          </navbar-link>

          <li>
            <router-link
              to="/pages"
              class="nav-link"
              active-class="active"
              aria-current="page"
              >Pages
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue';
export default {
  components: {
    NavbarLink,
  },
  inject: ['$pages', '$bus'],
  created() {
    this.pages = this.$pages.getAllPages();

    this.$bus.$on('page-updated', () => {
      this.pages = [...this.$pages.getAllPages()];
    });
  },

  computed: {
    publishedPages() {
      return this.pages.filter((p) => p.published);
    },
  },

  data() {
    return {
      pages: [],
    };
  },
};
</script>
