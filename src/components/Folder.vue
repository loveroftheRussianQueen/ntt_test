<script setup>
import { computed, onMounted, onUpdated, ref } from 'vue'
import { useIdStore } from '../store/id'

const props = defineProps({ folder: Object })
const emit = defineEmits(['pushId'])

const isOpen = ref(false)

const isFolder = computed(() => {
  return props.folder.subfolders
})

const idStore = useIdStore()

const toggle = () => {
  if (isFolder) {
    isOpen.value = !isOpen.value
  }
  idStore.id = props.folder.name
}
</script>

<template>
  <li>
    <div class="header" @click="toggle">
      <img src="../assets/folder.png" />
      {{ props.folder.name }}
      <span v-if="isFolder">{{ isOpen ? '-' : '+' }}</span>
    </div>
    <ul v-show="isOpen" v-if="isFolder">
      <Folder
        class="folder"
        v-for="(subfolder, index) in props.folder.subfolders"
        :key="index"
        :folder="subfolder"
      />
    </ul>
  </li>
</template>

<style lang="scss" scoped>
.header {
  display: flex;
  align-items: center;
  gap: 5px;
  img {
    width: 25px;
    height: 25px;
  }
}

ul {
  padding-left: 1em;
  line-height: 1.5em;
}

li {
  cursor: pointer;
  padding: 5px;
  list-style: none;
  font-size: 16px;
}
</style>
