<script lang="ts">
  import PageHead from "src/components/PageHead.svelte";
  import PostsContainer from "src/components/PostsContainer.svelte";

  export let data: any;

  $: posts = data?.posts ?? [];
  $: totalCount = data?.total;
</script>

<PageHead
  metaContent={{
    title: "AHRO Blog",
    description: "Read AHRO's latest articles on global health.",
  }}
/>
<PostsContainer {posts} category={undefined} {totalCount} />
