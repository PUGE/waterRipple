<template lang="pug">
  .water-ripple(@click.stop="rippleClick") {{text}}
</template>

<script>
  export default {
    props: {
      text: String
    },
    methods: {
      rippleClick (e) {
        const target = this.$el
        const rect = target.getBoundingClientRect()
        let ripple = target.childNodes[1]
        if (!ripple) {
          ripple = document.createElement('span')
          ripple.className = 'ripple'
          ripple.style.height = ripple.style.width = Math.max(rect.width, rect.height) + 'px'
          target.appendChild(ripple)
        }
        ripple.classList.remove('show')
        const top = e.pageY - rect.top - ripple.offsetHeight / 2 - document.body.scrollTop
        const left = e.pageX - rect.left - ripple.offsetWidth / 2 - document.body.scrollLeft
        ripple.style.top = top + 'px'
        ripple.style.left = left + 'px'
        ripple.classList.add('show')
        this.$emit('onClick')
      }
    }
  }
</script>

<style lang='less'>
  .water-ripple {
    position: relative;
    display: block;
    border: none;
    outline: none;
    letter-spacing: .2em;
    cursor: pointer;
    overflow: hidden;
    user-select: none;
    border-radius: 2px;
  }
  .ripple {
    position: absolute;
    background: rgba(0,0,0,.15);
    border-radius: 100%;
    transform: scale(0);
    pointer-events: none;
  }
  .ripple.show {
    animation: ripple .75s ease-out;
  }
  @keyframes ripple {
    to {
      transform: scale(2);
      opacity: 0;
    }
  }
</style>
