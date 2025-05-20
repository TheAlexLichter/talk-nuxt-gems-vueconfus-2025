<script setup lang="ts">
import { useQRCode } from '@vueuse/integrations/useQRCode'

const props = defineProps<{
  url: string,
  note?: string
}>()

const qrcode = useQRCode(props.url, {
  errorCorrectionLevel: 'H',
  margin: 3,
})
</script>

<template>
  <div class="flex flex-col items-center justify-center">
    <img v-if="url" class="mt-6 mb-2 rounded border w-32 h-32 !max-w-auto" :src="qrcode" :alt="`QR Code to ${url}`">
    <p class="flex flex-col justify-center items-center text-center"><slot>{{ note }}</slot></p>
  </div>
</template>