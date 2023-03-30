<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{title}}</h1>

          <message v-if="message" :message="message"/>

          <newNote :note="note" @addNote='addNote'/>

          <notes :notes="notes"/>
        </div>
      </section>
      
    </div>
  </div>

</template>

<script>
import message from '@/components/Message.vue'
import newNote from '@/components/NewNote.vue'
import notes from '@/components/Notes.vue'

export default {
  components:{
    message, notes, newNote
  },
  data() {
    return {
      title: 'Notes App',
      message: null,
      note:{
          title: '',
          description: ''
      },
      notes: [
          {
              title: 'First Note',
              description: 'This is first note',
              date: new Date(Date.now()).toLocaleString()
          },
          {
              title: 'Second Note',
              description: 'This is second note',
              date: new Date(Date.now()).toLocaleString()
          },
          {
              title: 'Third Note',
              description: 'This is third note',
              date: new Date(Date.now()).toLocaleString()
          }
      ]
    }
  },
  methods:{
            addNote(){
                //console.log(this.note)
                let note = this.note;

                if(note.title === '') {
                    this.message = 'title can`t be blank';
                    return false;
                }
                this.notes.push({
                    title: note.title,
                    description: note.description,
                    date: new Date(Date.now()).toLocaleString()
                })
                note.title = '';
                note.description = '';
                this.message = null;
            }
        }
  
}
</script>

<style>
</style>
