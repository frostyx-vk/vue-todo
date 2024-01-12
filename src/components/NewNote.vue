<template>
    <div class="new-note">
        <label>Заголовок</label>
        <input type="text" v-model="note.title">
        <label>Описание</label>
        <textarea v-model="note.descr"></textarea>
        <button class="btn btnPrimary" @click="addNote">Новая запись</button>
    </div>
</template>

<script>
export default {
    props: {
        note: {
            type: Object,
            required: true,
        },
    },
    methods: {
        addNote() {
            this.$emit('addNote', this.note)
        },
    },
}
</script>

<style lang="scss">
    .new-note {
        text-align: center;
    }
</style>