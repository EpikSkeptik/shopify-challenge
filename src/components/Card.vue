<template>
  <div class="card">
    <img :src="imgUrl" :alt="createTitle">
    <h2>{{ createTitle }}</h2>
    <p>{{ createDescription }}</p>
    <HeartIcon @click="likeClick" class="heart" :class="isLiked ? 'active' : '' " />    
  </div>
</template>

<script>
import { HeartIcon } from '@heroicons/vue/solid'

export default {
    props: ['packet'],
    components: {
        HeartIcon
    },
    data() {
        return {
            isLiked: false,
            description: null,
        }
    },
    methods: {
        likeClick() {
            this.isLiked = !this.isLiked
        }

    },
    computed: {
        createTitle() {
            return `${this.packet.rover.name} Rover - ${this.packet.camera.full_name}`
        },
        imgUrl() {
            return this.packet.img_src
        },
        createDescription() {
            return `Taken on ${this.packet.earth_date}`
        }
    }
}
</script>

<style scoped>
    .card {
        width: 400px;
        background: #fff;
        margin: 100px auto;
        border-radius: 10px;
    }

    .card img {
        max-width: 100%;
        border-radius: 10px 10px 0 0;
    }

    .card button {
        margin-bottom: 10px;
        background: none;
        padding: 0;
        border: none;

    }

    .heart {
        width: 30px;
        height: 30px;
        color:darkgrey;
        cursor: pointer;
        margin-bottom: 10px;

    }

    .heart.active {
        animation: like 2s ease forwards
    }


    @keyframes like {
        0% {color: darkgrey; transform: scale(1);}
        65% { transform: scale(2);}
        100% {color: red; transform: scale(1);}
    }
</style>