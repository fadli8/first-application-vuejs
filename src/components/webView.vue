<template>
 
    <div class="w-full py-2 bg-[#f1f1f1]">
        <div class="w-full flex ">
            <div class="w-full m-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                <h1 v-if="pages.length > 0" class="text-[30px] text-center">{{ pages[select].name }}</h1>
            </div>
        </div>

        <CreateForm :submitForm="creagePage" ></CreateForm>

        <!-- <div class="w-full h-[300px] flex ">
            <div class="w-full mx-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                You did it again! 
            </div>
            <div class="w-full mx-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                You did it again! 
            </div>
            <div class="w-full mx-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                You did it again! 
            </div>
        </div>

        <div class="w-full my-2 h-[50vh] flex">
            <div class="w-full mx-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                You did it again! 
            </div>
            
            <div class="w-full mx-2 border-[#d6d6d6] shadow bg-white rounded-sm p-3">
                You did it again! 
            </div>
        </div> -->
    </div>
</template>

<script>
import CreateForm from './CreateForm.vue';

export default {
    props: [
        "pages",
        "select",
        'creagePage'
    ],
    created() {
        this.getSelected();
    },
    methods: {
        getSelected() {
            console.log("this is from getSelected method with select:", this.select);
        },
    },
    components: { CreateForm }
}

</script>