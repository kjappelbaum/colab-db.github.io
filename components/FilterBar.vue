<template>
    <div class="w-full py-4 px-2 flex justify-between">
        <div class="flex justify-start items-center space-x-1">
            <span>{{ props.lenNotebooks }} Notebooks</span>
            <div v-if="q != ''" class="flex items-center space-x-1"><span>contain</span> <span
                    class="bg-gray-100 text-gray-800 text-xs font-semibold mr-2 px-2.5 py-0.5 rounded dark:bg-gray-700 dark:text-gray-300">{{
                            q
                    }}</span></div>
        </div>
        <div class="flex items-center">
            <Menu as="div" class="relative inline-block text-left">
                <div>
                    <MenuButton class="
                    group
                    inline-flex
                    justify-center
                    text-sm
                    font-medium
                    text-gray-700
                    hover:text-gray-900
                  ">
                        Sort
                        <ChevronDownIcon class="
                      flex-shrink-0
                      -mr-1
                      ml-1
                      h-5
                      w-5
                      text-gray-400
                      group-hover:text-gray-500
                    " aria-hidden="true" />
                    </MenuButton>
                </div>

                <transition enter-active-class="transition ease-out duration-100"
                    enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100"
                    leave-active-class="transition ease-in duration-75"
                    leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                    <MenuItems class="
                    origin-top-right
                    absolute
                    right-0
                    mt-2
                    w-40
                    rounded-md
                    shadow-2xl
                    bg-white
                    ring-1 ring-black ring-opacity-5
                    focus:outline-none
                  ">
                        <div class="py-1">
                            <MenuItem v-for="option in sortOptions" :key="option.name" v-slot="{ active }">
                            <a :href="option.href" :class="[
                                option.current
                                    ? 'font-medium text-gray-900'
                                    : 'text-gray-500',
                                active ? 'bg-gray-100' : '',
                                'block px-4 py-2 text-sm',
                            ]">
                                {{ option.name }}
                            </a>
                            </MenuItem>
                        </div>
                    </MenuItems>
                </transition>
            </Menu>

            <!-- <button type="button" class="p-2 -m-2 ml-5 sm:ml-7 text-gray-400 hover:text-gray-500">
                <span class="sr-only">View grid</span>
                <ViewGridIcon class="w-5 h-5" aria-hidden="true" />
            </button> -->
            <button type="button" class="
                p-2
                -m-2
                ml-4
                sm:ml-6
                text-gray-400
                hover:text-gray-500
                lg:hidden
              " @click="mobileFiltersOpen = true">
                <span class="sr-only">Filters</span>
                <FilterIcon class="w-5 h-5" aria-hidden="true" />
            </button>
        </div>
    </div>
</template>

<script setup>


import { ref } from "vue";
import {
    Dialog,
    DialogPanel,
    Disclosure,
    DisclosureButton,
    DisclosurePanel,
    Menu,
    MenuButton,
    MenuItem,
    MenuItems,
    TransitionChild,
    TransitionRoot,
} from "@headlessui/vue";
import { XIcon } from "@heroicons/vue/outline";
import {
    ChevronDownIcon,
    FilterIcon,
    MinusSmIcon,
    PlusSmIcon,
    ViewGridIcon,
} from "@heroicons/vue/solid";


const props = defineProps(['lenNotebooks', 'q'])

const mobileFiltersOpen = ref(false);

const sortOptions = [
    { name: "Most Stars", href: "#", current: true },
    { name: "Newest", href: "#", current: false },
    { name: "Most comments", href: "#", current: false },
];


</script>