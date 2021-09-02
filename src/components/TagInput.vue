<template>
    <div class="tag-input">
        <input v-model="newTag" type="text"
            @keydown.enter="addTag(newTag)"
            @keydown.prevent.tab="addTag(newTag)" 
            @keydown.delete="newTag.length || removeTag(tags.length -1)"
        />
        <ul class="tags">
            <li v-for="(tag, index) in tags" :key="tag" class="tag">
                {{ tag }}
                <button class="delete" @click="removeTag(index)">x</button>
            </li>
        </ul>
    </div>
</template>
<script>

import {ref} from vue

export default {

    setup(){
        const tags = ref([]);
        const newTag = ref('');
        const addTag = (tag) => {
            tags.value.push(tag);
            newTag.value;
        };
        const removeTag = (index) => {
            tags.value.splice(index, 1);
        };
        return { tags, newTag, addTag, removeTag };

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

input {
    width: 100%;
    padding: 10px;
}

.delete {
    color: white;
    background: none;
    outline: none;
    border: none;
    cursor: pointer;
}
</style>