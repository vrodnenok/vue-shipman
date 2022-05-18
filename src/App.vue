<script lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      links: [
        {
          name: "Home",
          href: "/",
        },
        {
          name: "About",
          href: "/about",
        },
        {
          name: "Todo",
          href: "/todo",
        },
      ],
    };
  },
  computed: {},
  methods: {},
});
</script>

<style>
.main-container {
  display: flex;
  gap: 5px;
  flex-wrap: wrap;
  height: 700px;
  font-family: Arial;
}

header {
  flex: 0 0 100%;
  height: 30px;
  background-color: #333;
  color: white;
}

nav {
  padding-top: 5px;
  float: left;
  color: white;
}

.rt-link {
  text-decoration: none;
  color: aquamarine;
  padding: 17px;
  border: aquamarine;
  justify-content: flex-end;
}

.rt-link-right {
  margin-left: auto;
  text-align: right;
}

.router-link-exact-active {
  font-weight: bold;
  color: white;
}
</style>

<template>
  <div class="main-container">
    <header>
      <nav>
        <RouterLink
          class="rt-link"
          v-for="link in links"
          :to="link.href"
          :key="link.name"
          >{{ link.name }}</RouterLink
        >
        <RouterLink class="rt-link" to="/login">Login</RouterLink>
      </nav>
    </header>
    <RouterView />
  </div>
</template>
