<template>
<header class="App-header">
    <h1>{{title}}</h1>
</header>
</template>

<script>
export default {
    name: 'Header',
    props: ['title'],
    setup() {}
}
</script>

<style scoped>
header {
    background-color: #6D2E46;
    top: 0px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    border-bottom: 10px solid #A26769;

}

header h1 {
    color: #EEE;
    font-size: 28px;
}
</style>
