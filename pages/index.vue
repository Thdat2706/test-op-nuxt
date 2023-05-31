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
        <p class="mt-2">
          Life is a struggle for single father Chris Gardner (Will Smith).
          Evicted from their apartment, he and his young son (Jaden Christopher
          Syre Smith) find themselves alone with no place to go. Even though
          Chris eventually lands a job as an intern at a prestigious brokerage
          firm, the position pays no money. The pair must live in shelters and
          endure many hardships, but Chris refuses to give in to despair as he
          struggles to create a better life for himself and his son.
        </p>
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
        {
          hid: "og:title",
          name: "og:title",
          content: "Mee title",
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
            "/static/favicon.png",
        },
        {
          hid: "og:description",
          name: "og:description",
          content:
            "Mee desc" },
      ],
    };
  },
};
</script>
