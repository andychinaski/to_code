<template>
    <div class="message">
        <p>{{message}}</p>
    </div>    
</template>

<script>
export default {
    props: {
        message: {
            type: String
        }
    }
}
</script>

<style lang="scss" scoped>
.message {
    text-align: center;
    padding: 20px;
}
p {
    color: rgb(160, 0, 0);
}
</style>
