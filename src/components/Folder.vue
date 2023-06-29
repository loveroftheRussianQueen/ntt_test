<script setup>
import { computed, onMounted, onUpdated, ref } from 'vue';

const props = defineProps({folder: Object});

const isOpen = ref(false);

const isFolder = computed(() =>{
    return props.folder.subfolders;
})

const toggle = () =>{
    if(isFolder){
        isOpen.value = !isOpen.value;   
    }
}
</script>

<template>
    <li>
        <div
          class="header"
          @click="toggle">
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
</style>