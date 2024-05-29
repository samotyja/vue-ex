<template>
  <h4>Edit {{ page.pageTitle }}</h4>

  <form
    action=""
    class="container mb-3"
  >
    <div class="row">
      <div class="col-md-8">
        <div class="mb-3">
          <label
            for=""
            class="form-label"
          >
            Page Title
          </label>
          <input
            type="text"
            class="form-control"
            v-model="page.pageTitle"
          />
        </div>
        <div class="mb-3">
          <label
            for=""
            class="form-label"
          >
            Content
          </label>
          <textarea
            type="text"
            class="form-control"
            rows="5"
            v-model="page.content"
          ></textarea>
        </div>
      </div>
      <div class="col">
        <div class="mb-3">
          <label
            for=""
            class="form-label"
          >
            Link Text
          </label>
          <input
            type="text"
            class="form-control"
            v-model="page.link.text"
          />
        </div>
        <div class="form-check">
          <label
            for=""
            class="form-check-label"
            >Published</label
          >
          <input
            type="checkbox"
            class="form-check-input"
            v-model="page.published"
          />
        </div>
      </div>
    </div>
    <div class="row mb-3">
      <div class="mb-3">
        <button
          class="btn btn-primary"
          @click.prevent="submit"
        >
          Edit
        </button>
        <button class="btn btn-secondary">Cancel</button>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useRoute } from 'vue-router';
import { inject } from 'vue';

const router = useRoute();
const pages = inject('$pages');

const { index } = defineProps(['index']);

let page = pages.getSinglePage(index);

function submit() {
  pages.editPage(index, page);
}
</script>
