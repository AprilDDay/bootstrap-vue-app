<template>
    <div>
        <div>
            <input v-model="newTitle" type="text" 
                @keydown.enter="addTitle(newTitle)"
            class="title" />
        </div>
        <div>
            <input v-model="newBlog" type="text"
            @keydown.enter="addBlog(newBlog)"
            class="paragraph"/>
        </div>
    </div>
</template>

<script>
import { ref } from vue;

export default{

    setup() {
        const newTitle = ref('');
        const newBlog = ref('');        
    },
    return (newTitle, newBlog);

}
</script>

<style scoped>
.title {
    font-size: 25px;
}

.paragraph {
    font-size: 12px;
}

</style>
