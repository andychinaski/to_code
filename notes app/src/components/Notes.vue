<template>
    <div class="notes">
        <div class="note" :class="{full: !grid}" v-for="(note, index) in notes" :key="index">
            <div class="note-header">
                <p>{{note.title}}</p>
                <p style="cursor:pointer;" @click="removeNote(index)">x</p>
            </div>
            <div class="note-body">
                <p>{{note.description}}</p>
                <span>{{note.date}}</span>
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    props: {
        notes: {
            type: Array
        },
        grid:{
            type: Boolean
        }
    },
    methods: {
        removeNote (index) {
            console.log(`Note id ${index} removed`)
            this.$emit('remove', index)
        }
    }
}
</script>

<style lang="scss">
.notes {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}
.note {
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: white;
    &.full{
        width: 100%;
    }
}
.note-header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1{
        font-size: 32px;
    }
    p {
        color: #3205ac;
        font-size: 22px;
    }
    svg {
        margin-right: 12px;
        color: #999;
        &:last-child{
            margin-right: 0;
        }
        cursor: pointer;
        &.active{
            color: #3205ac;
        }
    }
}
.note-body{
    p {
        margin: 20px 0;
    }
    span {
        font-size: 14px;
        color: #999;
    }
}
</style>