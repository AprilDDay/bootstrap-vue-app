<template>
    <div class="tag-input">
        <input v-model="newTag" type="text"
            @keydown.enter="addTag(newTag)"
            @keydown.prevent.tab="addTag(newTag)" 
            @keydown.delete="newTag.length || removeTag(tags.length -1)"
            :style="{ 'padding-left': `${paddingLeft}px`}"
        />
        <ul class="tags" ref="tagsUl">
            <li v-for="(tag, index) in tags" :key="tag" class="tag">
                {{ tag }}
                <button class="delete" @click="removeTag(index)">x</button>
            </li>
        </ul>
    </div>
</template>
<script>

import {ref, watch, nextTick, onMounted } from vue

export default {

    props:{
        modelValue: { type: Array, default: ()=> [] },
    },
    setup(props, {emit}){
        const tags = ref([props.modelValue]);
        const newTag = ref('');
        const addTag = (tag) => {
            tags.value.push(tag);
            newTag.value;
        };
        const removeTag = (index) => {
            tags.value.splice(index, 1);
        };
        const paddingLeft=ref(10);
        const tagsUl=ref(null);
        const onTagsChange = () => {
            const extraCushion = 15
            paddingLeft.value = tagsUl.value.clientWidth + extraCushion;
            tagsUl.value.scrollTo(tagsUl.value.scrollWidth, 0);
            emit("update:modelValue", tags.value)
        };
        watch(tags, ()=>nextTick(onTagsChange), {deep: true});
        onMounted(onTagsChange);
        return { tags, newTag, addTag, removeTag, paddingLeft, tagsUl, onTagsChange };
        //watch(tags, ()=>nextTick(setLeftPadding), {deep: true});
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
    position: absolute;
    top: 0;
    bottom: 0;
    left: 10px;
    max-width: 75%;
    overflow-x: auto;
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

.tag-input {
    position: relative;
}
</style>