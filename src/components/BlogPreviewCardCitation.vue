<script setup>
const props = defineProps({
    author_name: String,
    author_avatar: String,
});
</script>

<template>
    <div class="blog-card-citation">
        <a href="#" class="blog-card-citation__avatar">
            <img :src="`./${props.author_avatar}`" :alt="props.author_name" />
        </a>
        <a href="#" class="blog-card-citation__author">
            {{ props.author_name }}
        </a>
    </div>
</template>

<style scoped lang="scss">
.blog-card-citation {
    display: flex;
    flex-flow: row nowrap;
    justify-content: flex-start;
    align-items: center;
    gap: 1rem;
}

.blog-card-citation__avatar {
    display: block;
    --_size: 40px;
    width: var(--_size);
    height: var(--_size);
}

.blog-card-citation__author {
    font-size: 0.875rem;
    font-weight: 800;
}
</style>
