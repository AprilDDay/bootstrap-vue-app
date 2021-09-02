<template>
    <div class="tag-input">
        <ul class="tags">
            <li v-for="tag in tags" :key="tag" class="tag">
                {{ tag }}
            </li>
        </ul>
    </div>
</template>
<script>

import {ref} from vue

//import { defineComponent } from '@vue/composition-api'

/*
export default defineComponent({
    setup() {
        
    },
})
*/
export default {

    setup(){
        const tags = ref(['hello', 'world']);
        return { tags }
    }
}
    
</script>

<style scoped>
ul {
    list-style: none;
    display:flex;
    align-items: center;
    gap: 7px;
    margin: 0;
    padding: 0;
}

.tag {
    background: rgb(250, 104, 104);
    padding: 5px;
    border-radius: 4px;
    color: white;
    white-space: nowrap;
    transition: 0.1s ease background;
}
</style>