<template>
    <div class="card bg-transparent border-0 ">
        <img :src="image" class="card-img-top" :alt="title">
        <div class="card-body text-center">
            <h5 class="card-title">{{ title }}</h5>
            <h6 class="card-title">{{ subtitle }}</h6>

        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComponent',
    props: [
        'image',
        'archetype',
        'name',
    ]
}
</script>

<style lang="scss" scoped>

</style>