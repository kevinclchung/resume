<script setup lang="ts">
import ExampleThumbs from './example-thumbs.vue'
import { store } from '../../store';
const { xp } = defineProps({ xp: Object })
</script>

<template>
  <div :id="xp?.id" class="section" v-if="xp?.id !== null">
    <div :class="['logo', xp?.id]" />
    <h2>{{ xp?.title }}</h2>
    <h3>{{ xp?.company }}</h3>
    <span class="caption">{{ xp?.specificDates }}</span>
    <p>
    <ul>
        <li v-for="event in xp?.events">{{ event }}</li>
    </ul>
    </p>
    <template v-if="xp?.examples !== null">
      <h4>Examples</h4>
      <p v-if="typeof xp?.examples === 'string'">
        {{ xp.examples }}
      </p>
      <div v-else class="examples">
        <ExampleThumbs :xp="xp" />
      </div>
    </template>
  </div>
</template>

<style lang="scss" scoped>
.logo {
  height: calc(250px / 2);
  width: calc(250px / 2);
  margin: 0 1em 1em;
  border-radius: 50%;
  border: var(--resume-color) 3px solid;
  padding: 5px;

  @media only screen and (max-width: 800px) {
    height: calc(250px / 4);
    width: calc(250px / 4);
  }
  
  &::before {
    content: '';
    display: block;
    height: 100%;
    width: 100%;
    background-size: cover;
    background-position: -25%;
    border-radius: 50%;
  }
    &.xp-spoton::before {
      background-image: url('../../assets/images/resume/spoton-logo.png');
    }
    &.xp-tsys-cpay::before {
      background-image: url('../../assets/images/resume/tsys-cpay-logo.png');
    }
    &.xp-payhub::before {
      background-image: url('../../assets/images/resume/payhub-logo.png');
    }
    &.xp-wigix::before {
      background-image: url('../../assets/images/resume/wigix-logo.png');
    }
    &.xp-apple-store::before,
    &.xp-apple::before {
      background-image: url('../../assets/images/resume/apple-logo.png');
    }
    &.xp-n2k::before {
      background-image: url('../../assets/images/resume/n2k-logo.png');
    }
}
.examples {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
  margin: 1em 0;
}
</style>
