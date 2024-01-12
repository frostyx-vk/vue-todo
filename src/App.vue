<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>

          <message v-if="message" :message="message"/>
          <newNote :note="note" @addNote="addNote" />
          <notes :notes="notes" />

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
  components: {
    message,
    newNote,
    notes,
  },
  data() {
    return {
      title: 'Заметки',
      message: null,
      note: {
        title: '',
        descr: '',
      },
      notes: [
        {
          title: 'First',
          descr: 'For First',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Second',
          descr: 'For second',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Third',
          descr: 'For third',
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    }
  },
  methods: {
    addNote() {
      let { title, descr } = this.note;

      if (title === '') {
        this.message = 'Заголовок не заполнен!';
        return false;
      };

      this.notes.push({
        title: title,
        descr: descr,
        date: new Date(Date.now()).toLocaleString(),
      });

      this.massage = null;
      this.note.title = '';
      this.note.descr = '';
    }
  }
}
</script>

<style>
  .container h1 {
    text-align: center;
    padding-bottom: 30px;
  }
</style>
