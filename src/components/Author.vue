<template>
	<div class="author mx-auto text-center mb-8 sm:mb-16">
		<h1 v-if="showTitle" class="author__site-title mx-auto text-2xl">
			{{ $static.metaData.siteName }}
		</h1>

		<p class="author__intro opacity-75">
			{{ $static.metaData.siteDescription }}
		</p>
	</div>
</template>

<static-query>
query {
  metaData {
    siteName
    siteDescription
  }
}
</static-query>

<script>
export default {
	props: ['showTitle']
}
</script>

<style lang="scss">
.author {
	max-width: 500px;

	&__site-title {
		max-width: 400px;
	}
}
</style>
