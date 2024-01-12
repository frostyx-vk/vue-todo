<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1>{{ title }}</h1>

          <div class="message" v-if="message">
            <p>{{ message }}</p>
          </div>

          <div class="new-note">
            <input type="text" v-model="note.title">
            <textarea v-model="note.descr"></textarea>
            <button @click="addNote">Новая запись</button>
          </div>

          <div class="notes">
            <div class="note" v-for="(note, index) in notes" :key="index">
              <div class="note-header">
                <p>{{ note.title }}</p>
              </div>
              <div class="note-body">
                <p>{{ note.descr }}</p>
                <span>{{ note.date }}</span>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>

export default {
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
