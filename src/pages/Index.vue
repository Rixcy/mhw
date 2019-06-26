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
  monsters: allMonster {
    edges {
      node {
        id
        title
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
