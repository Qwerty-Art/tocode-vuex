<template>
  <div class="md-body">
    <Form @onSubmit="handleSubmit"></Form>
    <List @onRemove="handlerRemove" :items="notes"></List>
  </div>
</template>

<script>
import Form from "@/components/Notes/Form";
import List from "@/components/Notes/List";

export default {
  components: {
    Form,
    List
  },
  data() {
    return {
      // notes: ["task 1", "task 2", "task 3"],
       notes: [
        {
          title: 'Learn Vue 3',
          tags: ['work']
        },
         {
          title: 'Finish course',
          tags: ['work', 'home']
        },
       ],
    }
  },
  mounted() {
    this.getNotes()
  },
  watch: {
    notes: {
      handler(updateList) {
        localStorage.setItem('notes', JSON.stringify(updateList))
      },
      deep: true
    }
  },
  methods: {
    getNotes() {
      const localNotes = localStorage.getItem('notes')
      if(localNotes) {
        this.notes =JSON.parse(localNotes)
      }
    },
    handleSubmit(title) {
      const note = {
        title: title,
        tags: []
      }
      this.notes.push(note);
    },
    handlerRemove(index) {
      this.notes.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
</style>