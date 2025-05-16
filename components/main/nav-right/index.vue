<script setup lang="ts">
import { ref } from 'vue'

import { nextTick } from 'vue'

const scrollToSection = (id: string) => {
    nextTick(() => {
        setTimeout(() => {
            const el = document.getElementById(id)
            if (el) {
                el.scrollIntoView({ behavior: 'smooth', block: 'start' })
                history.replaceState(null, '', `${id}`)
            }
        }, 0)
    })
}

interface NavItem {
  label: string
  id: string
  children?: NavItem[]
}

const navItems = ref<NavItem[]>([
  {
    label: 'Automation and Conventions',
    id: '#automation-and-conventions'
  },
  {
    label: 'Server-Side Rendering',
    id: '#server-side-rendering',
    children: [
      { label: 'Server engine', id: '#server-engine' },
      { label: 'Production-ready', id: '#production-ready' },
      { label: 'Modular', id: '#modular' },
      { label: 'Architecture', id: '#architecture' }
    ]
  }
])

</script>

<template>
  <nav class="sticky top-(--ui-header-height) z-10 bg-default/75 lg:bg-[initial] backdrop-blur
         -mx-4 px-4 sm:px-6 sm:-mx-6 overflow-y-auto max-h-[calc(100vh-var(--ui-header-height))] 
         lg:col-span-2 order-first lg:order-last lg:backdrop-blur-none">
    <div
      class="pt-4 sm:pt-6 pb-2.5 sm:pb-4.5 lg:py-8 border-b border-dashed border-default lg:border-0 flex flex-col">
      <p
        class="group text-sm font-semibold flex-1 items-center gap-1.5 py-1.5 -mt-1.5 focus-visible:outline-primary hidden lg:flex">
        On this page
      </p>
      <div class="overflow-hidden focus:outline-none hidden lg:flex">
        <ul class="min-w-0 ms-2.5 ps-4 border-s border-default">
          <template v-for="item in navItems" :key="item.id">
            <li class="min-w-0 -ms-px">
              <a @click.prevent="scrollToSection(item.id)"
                class="group relative text-sm flex items-center focus-visible:outline-primary py-1 text-primary hover:text-default transition-colors"
              >
                <span class="truncate">{{ item.label }}</span>
              </a>
              <ul v-if="item.children" class="ms-3">
                <li v-for="child in item.children" :key="child.id" class="min-w-0 -ms-px">
                  <a
                    href="javascript:void(0)"
                    @click.prevent="scrollToSection(child.id)"
                    class="group relative text-sm flex items-center focus-visible:outline-primary py-1 text-muted hover:text-default transition-colors"
                  >
                    <span class="truncate">{{ child.label }}</span>
                  </a>
                </li>
              </ul>
            </li>
          </template>
        </ul>
      </div>
    </div>
  </nav>
</template>
<style scoped></style>