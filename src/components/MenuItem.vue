<template>
    <a :href="'#/'+page.url" 
        :class="{'bg-gray-900 text-white':isActive, 'text-gray-300':!isActive}"
        class="hover:bg-gray-700 hover:text-white rounded-md px-3 py-2 text-sm font-medium" aria-current="page"
        >
        {{page.title}}
    </a> 
    <!-- @click="clickLink(index)" -->
</template>

<script>
    export default {    
        props:[   
            "page", "isActive", "clickLink"
        ],
    }
</script>

<style scoped></style>