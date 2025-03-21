<script lang="ts" setup>
import { categories } from "@/constants/data";
import { Category } from "@/models/models";
import { ref } from "vue";

/**
 * Component State
 */

const selected = ref("category4");

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
  <div class="bg-white">
    <div class="relative isolate px-6 pt-14 lg:px-8">
      <div
        class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80"
        aria-hidden="true"
      >
        <div
          class="relative left-[calc(50%-11rem)] aspect-1155/678 w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-linear-to-tr from-blue-300 to-[#c0fffe] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]"
          style="
            clip-path: polygon(
              74.1% 44.1%,
              100% 61.6%,
              97.5% 26.9%,
              85.5% 0.1%,
              80.7% 2%,
              72.5% 32.5%,
              60.2% 62.4%,
              52.4% 68.1%,
              47.5% 58.3%,
              45.2% 34.5%,
              27.5% 76.7%,
              0.1% 64.9%,
              17.9% 100%,
              27.6% 76.8%,
              76.1% 97.7%,
              74.1% 44.1%
            );
          "
        ></div>
      </div>
      <div class="mx-auto px-20 py-32">
        <div class="hidden sm:mb-8 sm:flex sm:justify-center">
          <div
            class="relative rounded-full px-3 py-1 text-sm/6 text-gray-600 ring-1 ring-gray-900/10 hover:ring-gray-900/20"
          >
            ¡Deseando comenzar esta aventura!
            <a
              target="_blank"
              href="https://github.com/serlopDev"
              class="font-semibold text-indigo-600"
              ><span class="absolute inset-0" aria-hidden="true"></span>Para
              saber más sobre mí o mis proyectos<span aria-hidden="true"
                >&rarr;</span
              ></a
            >
          </div>
        </div>
        <div class="text-center">
          <h1
            class="text-6xl font-semibold tracking-tight text-balance text-gray-900"
          >
            Prueba técnica proceso de selección Bershka
          </h1>
          <div class="w-full mx-auto px-4">
            <div class="w-full mt-10 grid grid-cols-1">
              <div class="relative col-span-1 space-x-3">
                <div
                  class="absolute bottom-0 w-full h-px bg-gray-200"
                  aria-hidden="true"
                ></div>
                <ul
                  class="px-6 relative text-sm font-medium flex flex-nowrap -mx-4 sm:-mx-6 lg:-mx-8 overflow-x-scroll no-scrollbar"
                >
                  <li
                    v-for="(category, index) in outputs"
                    :key="index"
                    class="mr-6 last:mr-0 first:pl-4 sm:first:pl-6 lg:first:pl-8 last:pr-4 sm:last:pr-6 lg:last:pr-8"
                  >
                    <button
                      @click="selected = category"
                      class="block capitalize cursor-pointer pb-3 hover:text-blue-600 whitespace-nowrap"
                      :class="{
                        'text-blue-500 border-b-2 border-blue-500':
                          selected === category,
                      }"
                    >
                      categoría: {{ category }}
                    </button>
                  </li>
                </ul>
              </div>
              <div class="col-span-1 mx-auto mt-10">
                <div class="bg-white shadow-lg rounded-xl">
                  <div
                    class="w-full border-b border-slate-400 py-4 px-6 text-left text-black"
                  >
                    <strong>OUTPUT PATH</strong>
                  </div>
                  <div class="text-center px-20 py-10 text-xl">
                    {{ getCategoryPath(categories, selected) }}
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div
        class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]"
        aria-hidden="true"
      >
        <div
          class="relative left-[calc(50%+3rem)] aspect-1155/678 w-[36.125rem] -translate-x-1/2 bg-linear-to-tr from-blue-300 to-[#c0fffe] opacity-30 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]"
          style="
            clip-path: polygon(
              74.1% 44.1%,
              100% 61.6%,
              97.5% 26.9%,
              85.5% 0.1%,
              80.7% 2%,
              72.5% 32.5%,
              60.2% 62.4%,
              52.4% 68.1%,
              47.5% 58.3%,
              45.2% 34.5%,
              27.5% 76.7%,
              0.1% 64.9%,
              17.9% 100%,
              27.6% 76.8%,
              76.1% 97.7%,
              74.1% 44.1%
            );
          "
        ></div>
      </div>
    </div>
  </div>
</template>
