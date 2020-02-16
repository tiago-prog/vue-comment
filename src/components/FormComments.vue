<template>
  <form action class="form-todo form-group">
    <p>
      <input v-model="name" type="text" placeholder="nome" name="author" class="form-control" />
    </p>
    <p>
      <textarea v-model="message" name="message" placeholder="Comentário" class="form-control"></textarea>
    </p>
    <button v-on:click.prevent="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: ""
    };
  },
  methods: {
    addComment() {
      if (this.message.trim() === "") {
        return;
      }
      this.$emit("add-comment", {
        name: this.name,
        message: this.message
      });

      this.name = "";
      this.message = "";
    }
  }
};
</script>