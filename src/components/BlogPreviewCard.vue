<script setup>
import {ref, shallowRef} from "vue";

import BlogPreviewCardHeaderSvg from "./BlogPreviewCardHeaderSvg.vue";
import BlogTag from "./ui/BlogTag.vue";
import BlogPreviewCardCitation from "./BlogPreviewCardCitation.vue";

const blogCards = ref([
    {
        id: 1,
        title: "HTML & CSS foundations",
        tag: "Learning",
        tagLink: "#",
        date: "21 Dec 2023",
        image: shallowRef(BlogPreviewCardHeaderSvg),
        link: "#",
        description: "These languages are the backbone of every website, defining structure, content, and presentation.",
        author_avatar: "image-avatar.webp",
        author_name: "Greg Hooper",
    },
]);
</script>

<template>
    <div class="blog-card" v-for="blogCard in blogCards" :key="blogCard.id">
        <header class="blog-card__header">
            <component :is="blogCard.image" />
        </header>
        <div class="blog-card__tags-and-date">
            <div class="blog-card__tags">
                <BlogTag :tag="blogCard.tag" :tag-link="blogCard.tagLink" />
            </div>
            <div class="blog-card__date">Published {{ blogCard.date }}</div>
        </div>
        <div class="blog-card__details">
            <h2>
                <a :href="blogCard.link">{{ blogCard.title }}</a>
            </h2>
            <p>{{ blogCard.description }}</p>
        </div>
        <BlogPreviewCardCitation :author_name="blogCard.author_name" :author_avatar="blogCard.author_avatar" />
    </div>
</template>

<style scoped lang="scss">
.blog-card {
    display: grid;
    gap: 1rem;
    width: 100%;
    background: var(--clr-white);
    color: var(--clr-black);
    border-radius: var(--global-border-radius);
    position: relative;
    padding: var(--card-padding);

    @media screen and (min-width: 640px) {
        width: 380px;
        min-height: 528px;
    }

    &::after {
        display: block;
        content: "";
        width: 100%;
        height: 100%;
        border-radius: inherit;
        background-color: var(--clr-black);
        position: absolute;
        z-index: -1;
        --_offset: 0.5rem;
        top: var(--_offset);
        left: var(--_offset);
        transition: all 300ms ease;
    }

    &:hover::after {
        --_offset: 1rem;
    }
}

.blog-card__header {
    display: block;
    width: 100%;
    height: 176px;
    border-radius: calc(var(--card-padding) / 2);
    overflow: hidden;

    @media screen and (min-width: 60em) {
        height: 200px;
    }

    svg {
        width: 100%;
        height: 100%;
    }
}

.blog-card__tags {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 0.5rem;
}

.blog-card__date {
    font-size: 0.875rem;
}

.blog-card__details {
    h2 {
        a {
            font-weight: inherit;
        }
    }
}
</style>
