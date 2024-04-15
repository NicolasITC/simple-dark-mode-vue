<script setup>
import { ref } from "vue";

if (
  localStorage.theme === "dark" ||
  (!("theme" in localStorage) &&
    window.matchMedia("(prefers-color-scheme: dark)").matches)
) {
  document.documentElement.classList.add("dark");
} else {
  document.documentElement.classList.remove("dark");
}

const toggleDarkMode = ref(document.documentElement.className.includes("dark"));

const changeDarkMode = () => {
  toggleDarkMode.value = document.documentElement.classList.toggle("dark");
  toggleDarkMode.value
    ? (localStorage.theme = "dark")
    : (localStorage.theme = "light");
};
</script>
<template>
  <main
    class="flex flex-col items-center h-screen w-screen bg-slate-100 dark:bg-slate-700"
  >
    <h1 class="w-fi dark:text-white py-10 text-3xl">
      Dark mode simple example
    </h1>
    <button
      @click="changeDarkMode"
      class="py-2 px-3 bg-gray-500 rounded-md text-white dark:bg-gray-200 dark:text-gray-800 w-fit"
    >
      Switch theme
    </button>
  </main>
</template>
