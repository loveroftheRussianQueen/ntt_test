<script setup>
import { folders } from '../store/data'

const showSubFolder = (folder) => {
  if (folder.subfolders.length > 0) {
  }
}

const emit = defineEmits(['close'])
</script>

<template>
  <div class="modal">
    <div class="content">
      <button class="btn" @click="$emit('close')">Close</button>
      <div class="folders">
        <div v-for="folder in folders" style="color: #000">{{ folder.name }}</div>
      </div>
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
}
</style>
