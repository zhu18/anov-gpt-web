<script lang="ts" setup>
import { computed } from 'vue'
import { NAvatar } from 'naive-ui'
import { useUserStore, useAppStore } from '@/store'
import { isString } from '@/utils/is'


interface Props {
  image?: boolean
}
defineProps<Props>()

const userStore = useUserStore()

const avatar = computed(() => userStore.userInfo.avatar)

const appStore = useAppStore()

const theme = computed(() => appStore.theme)


console.log(appStore)
</script>

<template>
  <template v-if="image">
    <NAvatar v-if="isString(avatar) && avatar.length > 0" :src="avatar" />
    <NAvatar v-else round />
  </template>
  <span v-else class="text-[28px] dark:text-white">        
     <img style="width: 28px;" :src="theme=='dark'?'/logo.png':'/logo-dark.png'">
  </span>
</template>
