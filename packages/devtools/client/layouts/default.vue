<script setup lang="ts">
const client = useClient()
const waiting = computed(() => !client.value && !showConnectionWarning.value)
</script>

<template>
  <div bg-base of-hidden h-screen font-sans>
    <Notification />
    <div v-if="waiting" h-full w-full flex>
      <div flex="~ col" text-lg items-center ma animate-pulse>
        <div op50 i-carbon-circle-dash animate-spin text-4xl />
        Connecting...
      </div>
    </div>
    <div v-else grid="~ cols-[50px_1fr]" h-full of-hidden>
      <SideNav of-auto />
      <div h-full of-auto>
        <slot />
      </div>
    </div>
  </div>
</template>
