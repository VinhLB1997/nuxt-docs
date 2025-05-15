<script setup lang='ts'>
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
            <div class="data-[state=open]:animate-[collapsible-down_200ms_ease-out] 
                data-[state=closed]:animate-[collapsible-up_200ms_ease-out] 
                overflow-hidden focus:outline-none hidden lg:flex">
            </div>
        </div>
    </nav>

</template>
<style scoped></style>