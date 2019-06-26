<template>
  <div class="post-card content-box">
    <div class="post-card__content">
      <h2 class="post-card__title align-middle flex items-center">
        {{ monster.title }} <small class="text-sm ml-auto">{{ monster.type }}</small>
      </h2>
      <div class="block" v-if="monster.resistantTo.length > 0">
        <h3 class="text-sm">Resistant to:</h3>
        <span
          v-for="(resistance, key) in monster.resistantTo"
          :key="key"
          class="border-solid border border-white py-1 px-2 rounded-lg text-xs font-bold mr-1"
          v-html="resistance" />
      </div>
      <!-- {{ monster }} -->
    </div>
  </div>
</template>

<script>
export default {
  props: ['monster'],
}
</script>

<style lang="scss">
.post-card {
  margin-bottom: var(--space);
  position: relative;

  &__header {
    margin-left: calc(var(--space) * -1);
    margin-right: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    margin-top: calc(var(--space) * -1);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    &:empty {
      display: none;
    }
  }

  &__image {
    min-width: 100%;
  }

  &__title {
    margin-top: 0;
  }

  &:hover {
    transform: translateY(-5px);
    box-shadow: 1px 10px 30px 0 rgba(0,0,0,.1);
  }

  &__tags {
    z-index: 1;
    position: relative;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0.0;
    overflow: hidden;
    text-indent: -9999px;
    z-index: 0;
  }
}
</style>
