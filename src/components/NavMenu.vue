<template>
  <nav class="nav-menu">
    <h1>{{ header }}</h1>
    <p>Brought to you by {{ apiName }}</p>
  </nav>
</template>

<script>
export default {
    props: ['header', 'apiName'],


}
</script>

<style scoped>
    .nav-menu {
        text-align: left;
        margin: 0;
        padding: 10px 10px;
        background-color: rgb(66, 66, 66);
        color: rgb(207, 207, 207);
    }

    h1 {
        margin: 0;
    }
    
    p {
        margin: 10px 0;
    }

</style>