<script setup lang="ts">
import type { AssetInfo } from '~/../src/types'

const props = defineProps<{
  asset: AssetInfo
  folder?: string
}>()

const path = computed(() => {
  if (props.folder && props.asset.path.startsWith(props.folder))
    return props.asset.path.slice(props.folder.length)
  return props.asset.path
})
</script>

<template>
  <button flex="~ col gap-1" hover="bg-active" rounded p2 of-hidden items-center>
    <AssetPreview rounded w-30 h-30 border="~ base" :asset="asset" />
    <div of-hidden w-full text-center ws-nowrap truncate text-xs>
      {{ path }}
    </div>
  </button>
</template>
