<template>
  <Popup :left="left" :top="top" :cue="cue">
    <ul class="popup-menu">
      <li v-for="(item, index) in items" :key="index">
        <a :href="item.link" 
           class="popup-menu__link"
           @click="selectItem(index, $event)">
          <template v-if="item.icon">
            <i 
              class="popup-menu__icon fa" 
              :class="'fa-' + item.icon"
              aria-hidden="true">
              &nbsp;
            </i>
          </template>
          <template v-if="item.image">
            <img class="popup-menu__image" :src="item.image">&nbsp;
          </template>
          <span class="popup-menu__label">{{item.label}}</span>
        </a>
      </li>
    </ul>

  </Popup>

</template>

<script>
import Popup from '@/components/Popup';

export default {
  components: { Popup },
  props: ['items', 'left', 'top', 'cue'],
  methods: {
    selectItem(index, event) {
      event.preventDefault();
      this.$emit('selected', index);
    },
  },

};
</script>

<style lang="scss" scoped>
.popup-menu {
    list-style: none;
    margin: 0;
    min-width: 10em;
    background-color: #fff;
    font-size: 1rem;

  &--small {
    font-size: 1rem;
  }

  &--big {
    font-size: 1.6rem;
  }

  &__link {
    display: block;
    color: #555;
    font-family: 'Arial';
    padding: 0.5em 0.7em;
    text-decoration: none;
  }

  &__link:hover {
      background-color: #f3f3f3;
      color: #777;
  }

  &__image {
    width: 1.2em;
    height: 1.2em;
    border-radius: 50%;
    vertical-align: middle;
  }

  &__icon {
    vertical-align: middle;
    font-size: 1.2em;
  }

  &__label {
    font-size: 0.9em;
  }
}
</style>
