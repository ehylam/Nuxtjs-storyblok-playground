<template>
  <div class="container">
    <Content
      v-for="post in posts"
      to
      :title="post.title"
      :content="post.content"
      :image="post.image"
    />
  </div>
</template>

<script>
export default {
  components: {
    Content
  },
  // data() {
  //   return {
  //     posts: [
  //       {
  //         title: "GET AWAY FROM OUR FUCKING HOUSE AND OBEY THE LAWS BITCH",
  //         previewText: "WHAT THE FUCK YOU MAINLAND CHINESE FUCKS"
  //       },
  //       {
  //         title: "GET AWAY FROM OUR FUCKING HOUSE AND OBEY THE LAWS BITCHes",
  //         previewText: "WHAT THE FUCK YOU MAINLAND CHINESE FUCKers"
  //       }
  //     ]
  //   };
  // }

  asyncData(context) {
    return (
      context.app.$storyapi
        // where the data is getting pulled from
        .get("cdn/stories", {
          version: "draft",
          // selecting blog
          starts_with: "blog/"
        })
        .then(res => {
          return {
            posts: res.data.stories.map(bp => {
              return {
                // defining the data
                title: bp.content.title,
                content: bp.content.content,
                image: bp.content.image
              };
            })
          };
        })
    );
  }
};
</script>
