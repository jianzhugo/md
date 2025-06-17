<script setup lang="ts">
const props = defineProps({
  visible: {
    type: Boolean,
    default: false,
  },
})

const emit = defineEmits([`close`])

const contributors = [
  {
    name: `yanglbme`,
    imageUrl: `https://s2.loli.net/2024/11/20/8hpEtd9MaPyQR2n.jpg`,
    altText: `微信`,
  },
  {
    name: `yangfong`,
    imageUrl: `https://s2.loli.net/2024/11/20/1t9SdqnJpsGov2B.png`,
    altText: `支付宝`,
  },
]

function onUpdate(val: boolean) {
  if (!val) {
    emit(`close`)
  }
}
</script>

<template>
  <Dialog :open="props.visible" @update:open="onUpdate">
    <DialogContent>
      <DialogHeader>
        <DialogTitle>赞赏</DialogTitle>
      </DialogHeader>
      <div class="text-center">
        <p>扫码可支持本站</p>
        <p>若觉得项目不错，<a href="https://github.com/doocs/md" target="_blank">点我请支持原作者～</a></p>
        <div class="grid grid-cols-2 my-5 gap-4">
          <div v-for="contributor in contributors" :key="contributor.name" class="text-center">
            <img
              :src="contributor.imageUrl"
              :alt="contributor.altText"
              class="mx-auto"
              style="width: 90%; max-width: 200px;border-radius: 10%;"
            >
          </div>
        </div>
      </div>

      <DialogFooter class="sm:justify-evenly">
        <Button @click="emit('close')">
          关闭
        </Button>
      </DialogFooter>
    </DialogContent>
  </Dialog>
</template>
