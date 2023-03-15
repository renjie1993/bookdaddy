<script setup>
const props = defineProps({
  label: String,
  link: String,
  showIcon: {
    type: Boolean,
    default: () => true
  }
})
const emit = defineEmits(['click'])

const handleClick = () => {
  if (props.link) {
    // todo
  } else {
    event.preventDefault()
    emit('click')
  }
}
</script>

<template>
  <a class="link" :href="link" @click="handleClick">
    <Pointer width="18" v-if="showIcon"></Pointer>
    {{ label }}
  </a>
</template>

<style lang="scss" scoped>
.link {
  display: inline-block;
  background: #f16c5d;
  color: #ffffff;
  border-radius: 7px;
  padding: 5px 15px;
  margin-top: 10px;
  font-size: 18px;
}
</style>
