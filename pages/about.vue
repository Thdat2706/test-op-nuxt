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
        {
          hid: "og:title",
          name: "og:title",
          content: "about title",
        },
        {
          hid: "og:type",
          name: "og:type",
          content: "website",
        },
        {
          hid: "og:image",
          name: "og:image",
          content:
            "/favicon.ico",
        },
        {
          hid: "og:description",
          name: "og:description",
          content:
            "about desc" },
      ],
    };
  },
};
</script>
