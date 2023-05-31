<template>
  <h1>about page</h1>
</template>

<script>
export default {
  name: "IndexPage",
  head() {
    return {
      title: "The Pursuit of Happyness - Homepage",
      meta: [
        { hid: "og-type", property: "og:type", content: "website" },
        { hid: "og-title", property: "og:title", content: "My Title" },
        {
          hid: "og-image",
          property: "og:image",
          content: "/favicon.ico",
        },
        { hid: "og-desc", property: "og:description", content: "about desc" },
      ],
    };
  },
};
</script>
