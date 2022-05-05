<template>
    <div class="col text-center p-4">
    <div class="album p-3">
        <div class="img_album">
        <img :src="album.poster" :alt="album.title" />
        </div>
        <h3 class="py-3">{{ album.title }}</h3>
        <div class="info">
        <div class="author">
            {{ album.author }}
        </div>
        <div class="year">
            {{ album.year }}
        </div>
        </div>
    </div>
    </div>
</template>

<script>
    export default {
        name: "CardComponent",
        props: {
            album: Object,
        }
    };
</script>

<style lang="scss" scoped>
.col{
        height: 27rem;
        margin: 1rem 0;

    .album {
        min-height: 100%;
        background-color: $ds-primary;
        
        h3 {
            color: $ds-white;
        }
        .info {
            color: $ds-light-dark;
        }
    }
}
</style>