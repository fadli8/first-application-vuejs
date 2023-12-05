<template>
    <form>
        <div class="space-y-12 bg-white mx-2 px-3 rounded-md shadow">
            <div class="border-b border-gray-900/10 pb-12">
                <h2 class="text-base font-semibold leading-7 text-gray-900">Personal Information</h2>
                <p class="mt-1 text-sm leading-6 text-gray-600">Use a permanent address where you can receive mail.</p>

                <div class="mt-5 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
                    <div class="sm:col-span-3">
                        <label for="first-name" class="block text-sm font-medium leading-6 text-gray-900">Title</label>
                        <div class="mt-2">
                            <input type="text" v-model="title" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                        </div>
                    </div>

                    <div class="sm:col-span-3">
                        <label for="last-name" class="block text-sm font-medium leading-6 text-gray-900">Url</label>
                        <div class="mt-2">
                            <input type="text" v-model="url" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                        </div>
                    </div>

                    <div class="sm:col-span-3">
                        <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Content</label>
                        <div class="mt-2">
                            <input type="email" v-model="content" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                        </div>
                    </div>

                    <div class="sm:col-span-3">
                        <label for="country" class="block text-sm font-medium leading-6 text-gray-900">Publish</label>
                        <div class="mt-2">
                           <input type="checkbox" name="publish" :checked="published" v-model="published" />
                        </div>
                    </div>
                </div>
            </div>
            <div class=" flex items-center justify-end">
                <button type="button" class="text-sm font-semibold leading-6 text-gray-900">Cancel</button>
                <button :disabled="isFormInvalid" @click.prevent="validationForm" type="submit" class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Save</button>
            </div>
        </div>

    </form>
</template>

<script>
    export default{
        props:[
            "submitForm"
        ],
        computed:{
            isFormInvalid(){
                return !this.title || !this.url || !this.content; 
            }
        },
        data(){
            return {
                title:'',
                url:'',
                content:'',
                published:true
            }
        },
        methods:{
            validationForm(){
                if (!this.title || !this.url || !this.content) 
                {
                    alert("please fallup all the form")

                }else{
                    this.submitForm({title:this.title, url:this.url, content:this.content, publish:this.published});
                    this.clearcontent();
                }
            },

            clearcontent(){
                this.title = ''
                this.url = ''
                this.content = ''
                this.published = true;
            }
        }
    }
</script>
