<script setup>
import { onUnmounted, onUpdated, ref } from 'vue'
import { useIdStore } from '../store/id'
import { folders } from '../store/data'

import Folder from './Folder.vue'

const emit = defineEmits(['close'])
const idStore = useIdStore()
const currentId = ref(null)

const selectFolder = () => {
  currentId.value = idStore.id
  emit('close')
}
</script>

<template>
  <div class="modal">
    <div class="content">
      <button class="btn" @click="$emit('close')">Close</button>
      <ul class="folders">
        <button class="btn second" @click="selectFolder">OK</button>
        <Folder class="folder" :folder="folders" />
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.modal {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  background-color: rgba($color: #000000, $alpha: 0.6);
}

.content {
  position: relative;
  width: 50%;
  height: 500px;
  background-color: #070606;
  border-radius: 10px;
  padding: 20px;
}

.folders {
  background-color: #ece5e5;
  height: 100%;
  width: 100%;
  overflow-y: scroll;
}

.btn {
  cursor: pointer;
  position: absolute;
  top: 30px;
  right: 30px;
  padding: 10px 30px;
  font-size: 16px;
  color: #fff;
  background-color: #000000;
  border: 1px solid #000000;
  border-radius: 5px;
  transition: 0.3s ease-in-out;

  &:hover {
    background-color: #413b3b;
    border: 1px solid #413b3b;
  }

  &.second {
    right: 150px;
  }
}
</style>
