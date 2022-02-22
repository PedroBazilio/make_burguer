<template>
    <footer id="footer">
        <p>Monte seu hambúrguer! &copy; 2022</p>
    </footer>
</template>

<script>
export default {
    name: 'Footer'
}
</script>

<style scoped>
    #footer{
        height: 100px;
        background-color: rgb(241, 231, 236);
        border-top: 4px solid #111;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 30px;
        width: 100%;
        position: absolute;
        bottom: 0;
    }
</style>