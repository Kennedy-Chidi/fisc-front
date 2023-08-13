<template></template>

<script>
import HomeFooter from "../components/HomeFooter.vue";
import HomeNavigation from "../components/HomeNavigation.vue";
export default {
  components: { HomeNavigation },
  methods: {
    loadScript() {
      if (!process.server) {
        let el = document.getElementById("script");
        let el1 = document.getElementById("script1");

        if (el != undefined) {
          document.body.removeChild(el);
        }
        if (el1 != undefined) {
          document.body.removeChild(el1);
        }

        const script = document.createElement("script");
        const script1 = document.createElement("script");

        script.type = "text/javascript";
        script1.type = "text/javascript";

        script.src = "/script/home.js";
        script1.src = "/script/smartSupp.js";

        script.async = true;
        script1.async = true;

        script.id = "script";
        script1.id = "script1";
        const app = document.querySelector("#footer");
        if (app) {
          app.appendChild(script);
          app.appendChild(script1);
        } else {
          console.error("Could not find app node to append script element");
        }
      }
    },
  },
  mounted() {
    this.loadScript();
  },
};
</script>

<style></style>
