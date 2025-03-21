<script lang="ts" setup>
import { categories } from "@/constants/data";
import { Category } from "@/models/models";

/**
 * Component Methods
 */

const outputs = ["category4", "category2", "category5"];

const getCategoryPath = (categories: Array<Category>, categoryName: string) => {
  let path = "/";

  for (const category of categories) {
    if (category.name === categoryName) {
      return "/" + category.name;
    }

    if (category.subcategories.length) {
      path +=
        category.name + getCategoryPath(category.subcategories, categoryName);
    }
  }

  return path;
};
</script>
<template>
  <div
    class="bg-slate-50 py-20 w-screen grid gap-5 grid-cols-1 md:grid-cols-2 lg:grid-cols-3"
  >
    <div
      v-for="(category, index) in outputs"
      :key="index"
      class="col-span-1 px-20"
    >
      <h1 class="mb-3">
        Si introduces la categoría: <strong>{{ category }}</strong>
      </h1>
      <div
        class="bg-white mx-auto h-fit flex items-center justify-center shadow-lg border-2 border-slate-800 rounded-xl py-6 px-5 text-black font-semibold"
      >
        {{ getCategoryPath(categories, category) }}
      </div>
    </div>
  </div>
</template>
