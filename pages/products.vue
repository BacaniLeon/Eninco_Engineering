<template>
    <BackToTop/>
    <div class="products_intro_section">
      <Navigation/>
      <div class="products_intro_section_text">
        <h1>PRODUCTS</h1>
      </div>
    </div>

    <div class="products_and_new_releases">
      <div class="our_products">
      <h4>Our Products</h4>
      <h1>Eninco Originals</h1>
    </div>

    <div class="list_of_products_flex">
      <div
        class="list_of_products"
        v-for="product in products"
        :key="product.id"
        :style="{ backgroundImage: `url(${product.photo})`}"
      >
          <h2>{{ product.title }}</h2>
          <p>{{ product.paragraf }}</p>
      </div>
    </div>

    <div class="newly_released">
      <h1>Newly Released</h1>
    </div>

    <div class="list_of_new_releases_flex">
      <div
        class="list_of_new_releases"
        v-for="release in releases"
        :key="release.id"
        :style="{ backgroundImage: `url(${release.photo})`}"
      >
          <h2>{{ release.title }}</h2>
          <p>{{ release.paragraf }}</p>
      </div>
    </div>

    
</div>
        
    <Footer/>

</template>

<script setup>

  const products = [
  {
    title: "SUPER LOTUS",
    paragraf:
      "Wood Lacquer",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ETERNAL",
    paragraf:
      "Metal Coating",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ENIWALL",
    paragraf:
      "Wall Paint",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ACRYLCOAT",
    paragraf:
      "Plastic Coating",
    photo: "../resources/images/product.jpg",
  }
];

  const releases = [
  {
    title: "NESO",
    paragraf:
      "Traffic Paint",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "MEGASTONE",
    paragraf:
      "Adhesive Coating For Building Stones",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ACRYLIC SILICON",
    paragraf:
      "Exterior Paint",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "POOL PAINT",
    paragraf:
      "Waterproof And Quick-Dry Resin",
    photo: "../resources/images/product.jpg",
  }
];

</script>
  