<template>
   <div class="search">
     <input type="text" v-model="query" @keypress.enter="handleSearch">
     <button class="btn" @click="handleSearch">Search</button>
    </div>
</template>

<script>
export default {
    data() {
        return{
            query: ''
        }
    },
    methods:{
        handleSearch() {
       this.$emit('SearchRequested',this.query);
}
    }
}
</script>


<style>
.search input{
    padding: 5px 10px;
    border: 2px solid black;
    width: 300px;
    margin-left: 33%;
}
.search button{
margin: 10px;
background-color: gray; 
font-size: 15px;
border-radius: 10%;

}
</style>