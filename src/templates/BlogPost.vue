<template>
  <Layout>
    <div class="container markdown-body">
        <div class="level">
            <!-- <div class="level-left">
                <strong>Time To Read:</strong> &nbsp;
                <span> {{$page.post.timeToRead}} minute</span>
            </div> -->
            <div class="level-left">
                <h1 class="title is-3">{{$page.post.title}}</h1>
            </div>
        </div>
        <g-image
            v-if="$page.post.image" 
            :src="$page.post.image" alt="Placeholder image" 
            width="100%" fit="fill" 
        />
        <div id="content"  v-html="$page.post.content" />
    </div>
  </Layout>
</template>

<page-query>
query blogPost ($path: String!) {
  post: blogPost (path: $path) {
    title
    path
    timeToRead
    content
    image
  }
}
</page-query>

<script>
export default {
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style scoped>
#content .img {
  max-width: 50%;
}

img {
  display:block;
  margin-left:auto;
  margin-right:auto;
  max-height: 15em;
}

.markdown-body {
		box-sizing: border-box;
		min-width: 200px;
		max-width: 980px;
		margin: 0 auto;
		padding: 45px;
	}

	@media (max-width: 767px) {
		.markdown-body {
			padding: 15px;
		}
	}


</style>