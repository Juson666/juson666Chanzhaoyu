<script setup lang='ts'>
import type { CSSProperties } from 'vue'
import { computed, ref, watch } from 'vue'
import { NButton, NLayoutSider, useDialog } from 'naive-ui'
import List from './List.vue'
import Footer from './Footer.vue'
import { useAppStore, useChatStore } from '@/store'
import { useBasicLayout } from '@/hooks/useBasicLayout'
import { PromptStore, SvgIcon } from '@/components/common'
import { t } from '@/locales'

const appStore = useAppStore()
const chatStore = useChatStore()

const dialog = useDialog()

const { isMobile } = useBasicLayout()
const show = ref(false)

const collapsed = computed(() => appStore.siderCollapsed)

function handleAdd() {
  chatStore.addHistory({ title: 'New Chat', uuid: Date.now(), isEdit: false })
  if (isMobile.value)
    appStore.setSiderCollapsed(true)
}

function handleUpdateCollapsed() {
  appStore.setSiderCollapsed(!collapsed.value)
}

function handleClearAll() {
  dialog.warning({
    title: t('chat.deleteMessage'),
    content: t('chat.clearHistoryConfirm'),
    positiveText: t('common.yes'),
    negativeText: t('common.no'),
    onPositiveClick: () => {
      chatStore.clearHistory()
      if (isMobile.value)
        appStore.setSiderCollapsed(true)
    },
  })
}

const getMobileClass = computed<CSSProperties>(() => {
  if (isMobile.value) {
    return {
      position: 'fixed',
      zIndex: 50,
    }
  }
  return {}
})

const mobileSafeArea = computed(() => {
  if (isMobile.value) {
    return {
      paddingBottom: 'env(safe-area-inset-bottom)',
    }
  }
  return {}
})

watch(
  isMobile,
  (val) => {
    appStore.setSiderCollapsed(val)
  },
  {
    immediate: true,
    flush: 'post',
  },
)
</script>

<template>
  <NLayoutSider
    :collapsed="collapsed"
    :collapsed-width="0"
    :width="260"
    :show-trigger="isMobile ? false : 'arrow-circle'"
    collapse-mode="transform"
    position="absolute"
    bordered
    :style="getMobileClass"
    @update-collapsed="handleUpdateCollapsed"
  >
    <div class="flex flex-col h-full" :style="mobileSafeArea">
      <main class="flex flex-col flex-1 min-h-0">
        <div class="p-4">
          <NButton dashed block @click="handleAdd">
            {{ $t('chat.newChatButton') }}
          </NButton>
        </div>
        <div class="flex-1 min-h-0 pb-4 overflow-hidden">
          <List />
        </div>
        <div class="flex items-center p-4 space-x-4">
          <div class="flex-1">
            <NButton block @click="show = true">
              {{ $t('store.siderButton') }}
            </NButton>
          </div>
          <NButton @click="handleClearAll">
            <SvgIcon icon="ri:close-circle-line" />
          </NButton>
        </div>

<div class="p-4" style="padding: 0rem 1rem 1rem;"><button class="n-button n-button--default-type n-button--medium-type n-button--block" tabindex="0" type="button" style="--n-bezier: cubic-bezier(.4, 0, .2, 1); --n-bezier-ease-out: cubic-bezier(0, 0, .2, 1); --n-ripple-duration: .6s; --n-opacity-disabled: 0.5; --n-wave-opacity: 0.6; font-weight: 400; --n-color: #0000; --n-color-hover: #0000; --n-color-pressed: #0000; --n-color-focus: #0000; --n-color-disabled: #0000; --n-ripple-color: #18a058; --n-text-color: rgb(51, 54, 57); --n-text-color-hover: #36ad6a; --n-text-color-pressed: #0c7a43; --n-text-color-focus: #36ad6a; --n-text-color-disabled: rgb(51, 54, 57); --n-border: 1px solid rgb(224, 224, 230); --n-border-hover: 1px solid #36ad6a; --n-border-pressed: 1px solid #0c7a43; --n-border-focus: 1px solid #36ad6a; --n-border-disabled: 1px solid rgb(224, 224, 230); --n-width: initial; --n-height: 34px; --n-font-size: 14px; --n-padding: 0 14px; --n-icon-size: 18px; --n-icon-margin: 6px; --n-border-radius: 3px;"><!----><!---->
	 <a class="button btn gf_button gf_gs-button-element gf_gs-button---large" href="https://juson666.github.io/" target="" data-scroll-speed="2000" data-exc="" data-scroll-speed-sm="2000" data-scroll-speed-xs="2000"><span><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-语音版</font></font></span></a><div aria-hidden="true" class="n-base-wave"></div><div aria-hidden="true" class="n-button__border"></div><div aria-hidden="true" class="n-button__state-border"></div>
   </button>
</div>

<div class="p-4" style="padding: 0rem 1rem 1rem;"><button class="n-button n-button--default-type n-button--medium-type n-button--block" tabindex="0" type="button" style="--n-bezier: cubic-bezier(.4, 0, .2, 1); --n-bezier-ease-out: cubic-bezier(0, 0, .2, 1); --n-ripple-duration: .6s; --n-opacity-disabled: 0.5; --n-wave-opacity: 0.6; font-weight: 400; --n-color: #0000; --n-color-hover: #0000; --n-color-pressed: #0000; --n-color-focus: #0000; --n-color-disabled: #0000; --n-ripple-color: #18a058; --n-text-color: rgb(51, 54, 57); --n-text-color-hover: #36ad6a; --n-text-color-pressed: #0c7a43; --n-text-color-focus: #36ad6a; --n-text-color-disabled: rgb(51, 54, 57); --n-border: 1px solid rgb(224, 224, 230); --n-border-hover: 1px solid #36ad6a; --n-border-pressed: 1px solid #0c7a43; --n-border-focus: 1px solid #36ad6a; --n-border-disabled: 1px solid rgb(224, 224, 230); --n-width: initial; --n-height: 34px; --n-font-size: 14px; --n-padding: 0 14px; --n-icon-size: 18px; --n-icon-margin: 6px; --n-border-radius: 3px;"><!----><!---->
	 <a class="button btn gf_button gf_gs-button-element gf_gs-button---large" href="https://gpt1.juson.top/" target="" data-scroll-speed="2000" data-exc="" data-scroll-speed-sm="2000" data-scroll-speed-xs="2000"><span><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">GPT-插件版</font></font></span></a><div aria-hidden="true" class="n-base-wave"></div><div aria-hidden="true" class="n-button__border"></div><div aria-hidden="true" class="n-button__state-border"></div>
   </button>
</div>
				
      </main>
      <Footer />
    </div>
  </NLayoutSider>
  <template v-if="isMobile">
    <div v-show="!collapsed" class="fixed inset-0 z-40 w-full h-full bg-black/40" @click="handleUpdateCollapsed" />
  </template>
  <PromptStore v-model:visible="show" />
</template>
