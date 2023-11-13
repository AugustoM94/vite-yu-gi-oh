<template>
    <section>
        <div class="row gy-4" v-if="store.characterList.length > 0">
            <div class="col-12 col-md-4 col-lg-3" v-for="(item, index) in store.characterList" :key="item.id">
                <CardComponent :image="item.card_sets[2][2]" :title="item.name" :archetype="item.archetype" />
            </div>
        </div>
    </section>
</template>

<script>
import { store } from '../data/store.js';
import CardComponent from './CardComponent.vue';

export default {
    name: 'CharacterList',
    component: {
        CardComponent
    },
    data() {
        return {
            store
        };
    },
    components: { CardComponent }
}
</script>

<style lang="scss" scoped></style>