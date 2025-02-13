<template>

  <div>


    <!-- Static sidebar for desktop -->
    <div class="hidden lg:fixed lg:inset-y-0 lg:z-50 lg:flex lg:w-72 lg:flex-col">
      <!-- Sidebar component, swap this element with another sidebar if you like -->
      <div class="flex grow flex-col gap-y-5 overflow-y-auto bg-indigo-600 px-6">
       <div class="w-full p-2 mt-2 flex justify-center" >
          <span class=" text-white" style="font-size: 2rem;">W3</span>
       </div>
        <nav class="flex flex-1 flex-col ">
          <ul role="list" class="flex flex-1 flex-col gap-y-7">
            <li>
              <ul role="list" class="-mx-2 space-y-1">
                <li v-for="item in navigation" :key="item.name">
                  <a :href="item.href" :class="[item.current ? 'bg-indigo-700 text-white' : 'text-indigo-200 hover:bg-indigo-700 hover:text-white', 'group flex gap-x-3 rounded-md p-2 text-sm/6 font-semibold']">
                    <component :is="item.icon" :class="[item.current ? 'text-white' : 'text-indigo-200 group-hover:text-white', 'size-6 shrink-0']" aria-hidden="true" />
                    {{ item.name }}
                  </a>
                </li>
              </ul>
            </li>
           
          
          </ul>
        </nav>
      </div>
    </div>

    <div class="sticky top-0 z-40 flex items-center gap-x-6 bg-indigo-600 px-4 py-4 shadow-sm sm:px-6 lg:hidden">
      <button type="button" class="-m-2.5 p-2.5 text-indigo-200 lg:hidden" @click="sidebarOpen = true">
        <span class="sr-only">Open sidebar</span>
        <Bars3Icon class="size-6" aria-hidden="true" />
      </button>
      <div class="flex-1 text-sm/6 font-semibold text-white">Dashboard</div>
      <a href="#">
        <span class="sr-only">Your profile</span>
      </a>
    </div>

    <main class="py-2 lg:pl-72">
      <div class="px-4 ">
        <stocktable/>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue'
import stocktable from '~/components/stocktable.vue'
import {
  Bars3Icon,
 
  XMarkIcon,
} from '@heroicons/vue/24/outline'

const navigation = [
  { name: 'Dashboard', href: '#', current: true },
  { name: 'Leadger', href: '#', current: false },

]

const sidebarOpen = ref(false)
</script>