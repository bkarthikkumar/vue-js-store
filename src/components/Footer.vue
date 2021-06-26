<template>
 <footer
    class="text-center">
    <span class="text-sm">Copyright &COPY; {{year()}} B Karthik Kumar</span>
  </footer>
</template>
<script>
export default {
    name   : "Footer File",
    methods: {
        year(){
            return new Date().getFullYear();
        }
    }
}
</script>
<style scoped>
footer {
    background: #343a40;
    color     : #fff;
    /* position: fixed; */
    bottom : 0;
    width  : 100%;
    padding: 15px;
}
</style>