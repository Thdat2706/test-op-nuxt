<template>
  <main class="w-full max-w-4xl mx-auto px-5">
    <nav class="py-5 text-center font-bold text-lg">Nuxt Open Graph Demo</nav>
    <section class="overflow-hidden rounded-xl">
      <img
        src="https://res.cloudinary.com/dpkreativ/image/upload/v1648291772/nuxt-open-graph-demo/webANXPursuitOfHappynessA_azzusy.jpg"
        alt="The Pursuit of Happyness: cover image"
        class="object-cover"
      />
    </section>
    <section class="py-5">
      <div class="lg:flex justify-between items-center">
        <h1 class="font-bold text-2xl lg:text-4xl my-1">
          The Pursuit of Happyness
        </h1>
        <a href="https://www.imdb.com/title/tt0454921/">
          <button class="bg-yellow-400 font-black text-xl p-1 rounded shadow">
            <p class="animate-pulse">IMDb</p>
          </button>
        </a>
      </div>
      <div class="mt-5">
        <h2 class="font-semibold text-lg">Film Synopsis</h2>
        <p class="mt-2">123</p>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: "IndexPage",
  head() {
    return {
      title: "The Pursuit of Happyness - Homepage",
      meta: [
        { hid: "og-title", property: "og:title", content: "Mee Title" },
        { hid: "og-type", property: "og:type", content: "website" },
        {
          hid: "og-image",
          property: "og:image",
          content:
            "https://images.unsplash.com/photo-1575936123452-b67c3203c357?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1740&q=80",
        },
        { hid: "og-desc", property: "og:description", content: "Mee desc" },
        { hid: "t-type", name: "twitter:card", content: "summary" },
      ],
    };
  },
};
</script>
