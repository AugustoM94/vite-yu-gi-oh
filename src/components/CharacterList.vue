<template>
    <section>
        <div class="bg-black py-3 px-2">
           <span class="text-white">Found {{ characters.length }} card</span>
        </div>
        <div class="row gy-1" v-if="store.characterList.length > 0">
            <div class=" card-width col-12 col-md-4 col-lg-2 d-flex flex-wrap" v-for="(item, index) in store.characterList" :key="item.id">
                <CardComponent :image="item.card_images[0].image_url" :name="item.name" :archetype="item.archetype" />
            </div>
        </div>
    </section>
</template>

<script>
import { store } from '../data/store.js';
import CardComponent from './CardComponent.vue';

export default {
    name: 'CharacterList',
    props: {
        characters: Array,
    },
    data() {
        return {
            store
        };
    },
    components: { CardComponent }
}
</script>

<style lang="scss" scoped>
.card-width {
    width: calc(100% / 5);
}
</style>