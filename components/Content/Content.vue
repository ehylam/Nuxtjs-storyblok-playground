<template>
  <section class="content_block">
    <article class="content_block__wrapper">
      <h1>{{title}}</h1>
      <p>{{content}}</p>
    </article>
    <!-- HELP: if the image component is true then input the backgroundImage -->
    <article class="image_block__wrapper" :style="{backgroundImage: 'url('+ image +')'}"></article>
  </section>
</template>

<script>
export default {
  // What properties this component will receive
  props: {
    title: {
      type: String,
      required: true
    },
    content: {
      type: String,
      required: true
    },
    image: {
      type: String,
      required: true
    }
  }
};
</script>
