<template>
    <div class="new-note">
        <label>Title</label>
        <input v-model="note.title" type="text">
        <label>Description</label>
        <textarea v-model="note.description"></textarea>
        <button class="btn btnPrimary" @click="addNote">New note</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object
        }
    },
    methods: {
        addNote(){
            this.$emit('addNote', this.note)
        }
    }
}
</script>

<style lang="scss" scoped>
.new-note {
    text-align: center;
}
button{
    margin: 1em;
}
</style>