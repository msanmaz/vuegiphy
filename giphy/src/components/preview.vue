<template>
    <div>
        <ul>
            <li v-for="gifs in gifs" :key="gifs">
                <img :src="gifs.images.fixed_height.url">
            
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: [ 'gifs']
}
</script>

<style>
li{
    list-style-type: none;
    float: left;
    
}
</style>