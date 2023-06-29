<script setup>
import { ref } from 'vue'
import Modal from './components/Modal.vue'

const isShowModal = ref(false)

const openModal = () => {
  isShowModal.value = true
}

const closeModal = () => {
  isShowModal.value = false
}
</script>

<template>
  <div class="main">
    <button class="btn" @click="openModal">Открыть</button>
    <Modal v-if="isShowModal" @close="closeModal" />
  </div>
</template>

<style scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100%;
}
.btn {
  cursor: pointer;
  padding: 10px 20px;
  background-color: rgb(62, 199, 114);
  color: #fff;
  font-size: 22px;
  border: 1px solid rgb(62, 199, 114);
  border-radius: 10px;
  transition: ease-in 0.3s;
}

.btn:hover {
  background-color: rgb(52, 170, 97);
}
</style>
