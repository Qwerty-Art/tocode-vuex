<template>
  <div class="note-form__wrapper">
    <form class="note-form" @submit.prevent="onSubmit">
      <textarea required v-model.trim="value" placeholder="Type ur note" />
      <TagsList @onItemClick="handlerTagClick" :items="tags"></TagsList>
      <button class="btn btnPrimary" type="submit">Add new note</button>
    </form>
  </div>
</template>

<script>
import TagsList from '@/components/UI/TagsList'

export default {
  components: {
    TagsList
  },
  data() {
    return {
      value: '',
      tags: ['home', 'work', 'travel']
    }
  },
  methods: {
    onSubmit() {
      this.$emit('onSubmit', this.value)
      this.value = ""
    },
    handlerTagClick(tag) {
      console.log(tag)
    }
  }
}
</script>

<style lang="scss" scoped>
.note-form {
  display: flex;
  flex-direction: column;
  max-width: 600px;
  width: 100%;
  textarea {
    margin-bottom: 0;
  }
}

.note-form__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>