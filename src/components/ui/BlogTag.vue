<script setup>
const props = defineProps({
    tag: String,
    tagLink: String,
});
</script>

<template>
    <a :href="props.tagLink" class="tag">{{ props.tag }}</a>
</template>

<style scoped lang="scss">
.tag {
    display: inline-block;
    padding: var(--tag-padding);
    border-radius: var(--tag-border-radius);
    background-color: var(--clr-yellow);
    color: var(--clr-black);
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.5px;
    transition: all 300ms ease;

    &:hover {
        background-color: var(--clr-dark-yellow);
    }
}
</style>
