<template>
  <Layout :show-logo="false">
    <Author :show-title="true" />

    <div class="posts">
      <MonsterCard v-for="edge in $page.monsters.edges" :key="edge.node.id" :monster="edge.node" />
    </div>

  </Layout>
</template>

<page-query>
{
  posts: allPost {
    edges {
      node {
        id
        title
        path
        tags {
          id
          title
          path
        }
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        coverImage (width: 770, height: 380, blur: 10)
        ...on Post {
            id
            title
            path
        }
      }
    }
  },
  monsters: allMonster {
    edges {
      node {
        id
        name
        location
        type
        description
        resistantTo
        standardDamage
        bonusDamage
        immuneTo
        tailSeverable
      }
    }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import MonsterCard from '~/components/MonsterCard.vue'

export default {
  components: {
    Author,
    MonsterCard
  },
  metaInfo: {
    title: 'Home'
  }
}
</script>
