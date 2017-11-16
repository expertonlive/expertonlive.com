<template>
  <div class="popup">
    <span class="popup__cue"></span>
    <slot></slot>
  </div>
</template>


<script>

function findElementGeometry(element) {
  const geometry = {};
  geometry.height = element.offsetHeight;
  geometry.width = element.offsetWidth;

  let curleft = 0;
  let curtop = 0;
  if (element.offsetParent) {
    /* eslint-disable no-cond-assign */
    do {
      curleft += element.offsetLeft;
      curtop += element.offsetTop;
    /* eslint-disable no-param-reassign */
    } while ((element = element.offsetParent) !== null);
  }

  geometry.left = curleft;
  geometry.top = curtop;

  return geometry;
}

export default {

  // props: ['left', 'right'],
  props: {
    left: {
      type: Number,
      default: 0,
    },
    top: {
      type: Number,
      default: 0,
    },
    cue: {
      type: String,
      default: 'left',
      validator: (value) => {
        const validCues = ['left', 'right', 'center'];
        return validCues.indexOf(value) !== -1;
      },
    },
  },

  data() {
    return {
      cueElement: null,
      targetElement: null,
    };
  },

  mounted() {
    this.$el.style.visibility = 'hidden';
    this.cueElement = this.$el.firstChild;
    this.targetElement = this.$el.parentElement;
    this.calculatePositions();
    this.boundToggleMethod = this.toggle.bind(this);
    this.targetElement.addEventListener('click', this.boundToggleMethod);
  },

  beforeDestroy() {
    // manual cleanups
    this.targetElement.removeEventListener('click', this.boundToggleMethod);
  },

  methods: {
    calculatePositions() {
      // get dimensions
      const elementGeometry = findElementGeometry(this.$el);
      const targetElementGeometry = findElementGeometry(this.targetElement);
      // set element position
      this.$el.style.left = `${targetElementGeometry.left + this.left + 5}px`;
      this.$el.style.top = `${targetElementGeometry.top +
                              targetElementGeometry.height + this.top + 10}px`;
      // place the cue
      if (this.cue === 'left') {
        this.cueElement.style.left = '20px';
      } else if (this.cue === 'right') {
        this.cueElement.style.left = `${elementGeometry.width - 35}px`;
      } else if (this.cue === 'center') {
        this.cueElement.style.left = `${(elementGeometry.width / 2) - 5}px`;
      }
    },

    toggle() {
      if (this.$el.style.visibility === 'hidden') {
        this.$el.style.visibility = 'visible';
      } else {
        this.$el.style.visibility = 'hidden';
      }
    },

  },

};

</script>

<style lang="scss" scoped>
// popup
.popup {
  position: absolute;
  min-width: 150px;
  min-height: 150px;
  border: 1px solid #ddd; 
  /*box-shadow: 0 1px 7px rgba(0,0,0,.05);*/
  box-shadow: 0 1px 1px #aaa;
  font-size: 1rem;
  z-index: 10;
  padding-top: 0.3rem;
  background-color: #fff;

  &__cue {
    display: inline-block;
    padding: 0.4em;
    position: absolute;
    top: -0.5em;
    left: 4em;
    z-index: -1;
    color: #fff;
    background: #fff;
    transform: rotate(-135deg);

    border: 1px solid #ddd;
    border: 1px solid #ddd;
    border-left: none;
    border-top: none;
  }
}
</style>
