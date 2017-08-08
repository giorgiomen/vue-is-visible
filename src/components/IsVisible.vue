<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default{
    props: ['event'],
    data: function () {
      return {
        visible: false,
      }
    },
    methods: {
      handleScroll () {
        var offset = this.offset(this.$el)
        var scrollPosition = this.scrollPosition()
        var scrollPositionTop = scrollPosition.top
        var scrollPositionLeft = scrollPosition.left
        if ((scrollPositionTop + window.innerHeight) >= offset.top && (scrollPositionLeft + window.innerWidth) >= offset.left) {
          var oldStatus = this.visible
          this.visible = true
          this.emit(oldStatus, this.visible)
        } else {
          this.visible = false
        }
      },
      emit (oldStatus, newStatus) {
        if (oldStatus !== newStatus) {
          this.$emit(this.event)
        }
      },
      scrollPosition () {
        var scrollLeft = window.pageXOffset || document.documentElement.scrollLeft
        var scrollTop = window.pageYOffset || document.documentElement.scrollTop
        return { top: scrollTop, left: scrollLeft }
      },
      offset (el) {
        var rect = el.getBoundingClientRect()
        var scrollPosition = this.scrollPosition()
        return { top: rect.top + scrollPosition.top, left: rect.left + scrollPosition.left }
      },
    },
    created () {
      window.addEventListener('scroll', this.handleScroll)
    },
    destroyed () {
      window.removeEventListener('scroll', this.handleScroll)
    },
  }
</script>
