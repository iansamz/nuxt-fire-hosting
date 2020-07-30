<template>
  <div class="body-inner">
    <topbar />

    <abovenav />

    <navbar />

    <nuxt />

    <foot />
    <copyright />
  </div>
</template>

<script>
import Topbar from "~/components/layouts/Topbar.vue";
import Abovenav from "~/components/layouts/Header.vue";
import Navbar from "~/components/layouts/Navbar.vue";
import Foot from "~/components/layouts/Footer.vue";
import Copyright from "~/components/layouts/Copyright.vue";

export default {
  components: {
    Topbar,
    Abovenav,
    Navbar,
    Foot,
    Copyright
  }
};
</script>
