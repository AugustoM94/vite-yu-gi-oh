<template>
 <div class="card-container h-100">
     <div class="card h-100  text-center " style="width: 13rem;">
                  <img :src="image" class="card-img-top" :alt="name">
             <div class="card-body">
                    <h6 class="card-text text-white">{{ name }}</h6>
                    <small class="px-1 ">{{ archetype }}</small>
                 </div>
             </div>
        </div>
      <div>
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
.card {
    background-color:  #D48F38;
}
h6 {
    font-size: 0.7rem;
}
small {
    font-size: 0.8rem;
}
</style>