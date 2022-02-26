<template>
  <div id="users">
    <h1 class="my-5">Users</h1>

    <table class="table">
      <thead>
        <tr>
          <th scope="col">
            <span @click="sort('name')">
              Name
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-arrow-down-short"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a.5.5 0 0 1 .5.5v5.793l2.146-2.147a.5.5 0 0 1 .708.708l-3 3a.5.5 0 0 1-.708 0l-3-3a.5.5 0 1 1 .708-.708L7.5 10.293V4.5A.5.5 0 0 1 8 4z"
                />
              </svg>
            </span>
          </th>
          <th scope="col">
            <span @click="sort('age')">
              Age
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-arrow-down-short"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a.5.5 0 0 1 .5.5v5.793l2.146-2.147a.5.5 0 0 1 .708.708l-3 3a.5.5 0 0 1-.708 0l-3-3a.5.5 0 1 1 .708-.708L7.5 10.293V4.5A.5.5 0 0 1 8 4z"
                />
              </svg>
            </span>
          </th>
          <th scope="col">
            <span @click="sort('gender')">
              Gender
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-arrow-down-short"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a.5.5 0 0 1 .5.5v5.793l2.146-2.147a.5.5 0 0 1 .708.708l-3 3a.5.5 0 0 1-.708 0l-3-3a.5.5 0 1 1 .708-.708L7.5 10.293V4.5A.5.5 0 0 1 8 4z"
                />
              </svg>
            </span>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in userSort" :key="user.id">
          <th scope="row">{{ user.name }}</th>
          <td>{{ user.age }}</td>
          <td>{{ user.gender }}</td>
        </tr>
      </tbody>
    </table>

    <p class="small">
      Debug: sort - {{ currentSort }}, dir - {{ currentSortDir }}
    </p>
  </div>
</template>

<script>
// api - https://tocode.ru/static/_secret/courses/1/usersCrmApi.php

import axios from "axios";

export default {
  data() {
    return {
      users: [],
      currentSort: "name",
      currentSortDir: "asc",
    };
  },

  created() {
    axios
      .get("https://tocode.ru/static/_secret/courses/1/usersCrmApi.php")
      .then((response) => {
        this.users = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },

  computed: {

      // Разобрать этот код, пока ничего не понятно про сортировку

      userSort() {
          return this.users.sort((a, b) => {
              let mod = 1
              if(this.currentSortDir === 'desc') {
                  mod = -1
              }
              if(a[this.currentSort] < b[this.currentSort]) {
                  return -1 * mod
              }

              if(a[this.currentSort] > b[this.currentSort]) {
                  return 1 * mod
              }

              return
          })
      }
  },

  methods: {

      // Разобрать этот код, пока ничего не понятно про сортировку

      sort(evt) {
          if(evt === this.currentSort) {
              this.currentSortDir = this.currentSortDir === 'asc' ? 'desc' : 'asc'
          }
          this.currentSort = evt
      }
  },
};
</script>

<style scoped>
th span {
    cursor: pointer;
}
</style>
