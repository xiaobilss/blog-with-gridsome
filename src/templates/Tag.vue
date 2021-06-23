<template>
  <Layout>
    <!-- Page Header -->
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1># {{ $page.tag.title }}</h1>
              <!-- <span class="subheading">A Blog Theme by Start Bootstrap</span> -->
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div
            class="post-preview"
            v-for="posts in $page.tag.posts"
            :key="posts.id"
          >
            <g-link :to="'/post/' + posts.id">
              <h2 class="post-title">
                {{ posts.title }}
              </h2>
            </g-link>
            <!-- <p class="post-meta">
              {{ posts.content }}
              <a href="#">yuqi</a>
              {{ posts.updated_at }}
            </p>
            <p>
              <span v-for="tag in posts.tags" :key="tag.id">
                <g-link :to="'/tag/' + tag.id">{{ tag.title }}</g-link>
                &nbsp;&nbsp;&nbsp;
              </span>
            </p> -->
          </div>
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  tag : strapiTag (id: $id){
    id
    title
    posts {
      id
      title
    }
  }
}
</page-query>

<script>
export default {
  name: "tag",
};
</script>