<template>
  <div class="header row expanded">
    <div class="small-6 columns">
      <div class="logo">
        <a href="/" class="logo__link">Expert<em class="logo__highlight">On</em>Live</a>
      </div>
    </div>
    <div class="small-6 columns">
        <ul class="header__right">
          <li class="header__item">
            <a class="header__link header__search-cue" 
              href="/search">
              <i class="fa fa-search"></i>
            </a>
          </li>
            <li class="header__item">
            <a ui-sref="auth" class="header__link">
              <i class="fa fa-user-o" aria-hidden="true"></i>&nbsp;Sign in
            </a>
          </li>
          <li class="header__item">
              <a href="#">
              <img class="user-avatar user-avatar--small" src="../assets/images/default-user.png" alt="">
              <PopupMenu 
                :left="-120" 
                :top="20" 
                :cue="'right'"
                :items="menuItems"
                @selected="onSelected">
              </PopupMenu>
              </a>
          </li> 
        </ul>
    </div>
  </div> <!-- end of top-bar/header -->
</template>

<script>
import PopupMenu from '@/components/PopupMenu';

export default {
  // name: 'Header',
  components: { PopupMenu },
  data() {
    return {
      menuItems: [
        { icon: 'user-circle-o', label: 'User', link: '#' },
        { icon: 'dashboard', label: 'Dashboard', link: '/dash' },
        { icon: 'sign-out', label: 'Logout', link: '#' },
      ],
    };
  },

  methods: {
    onSelected(item) {
      console.log('clicked item: ', item);
    },
  },
};
</script>



<style lang="scss">

.header{
  font-size: 1rem;
  padding: 0.5rem;
  border-bottom: 1px solid rgb(238, 238, 238);

  &__right {
    padding: 0;
    margin: 0;
    list-style: none;
    float: right;
  }
  &__item {
    display: inline-block;
    line-height: 1;
    margin-left: 2.5rem;
  }

  &__link {
    color: #696969;
    // line-height: 3em;
    font-weight: 600;
    display: inline-block; 
    padding: 0.5em 0.4em!important;           
  }

  &__search-cue {
    font-size: 1.5em;
    color: $primary-color;
  }

  &--icon {
    vertical-align: top;
  }

}

</style>
