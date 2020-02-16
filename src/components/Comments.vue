<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormComments v-on:add-comment="addComment" />

    <div class="list-group">
      <p v-if="comments.length <= 0">Sem comentários...</p>
      <div
        class="list-group-item mb-3"
        v-else
        v-for="(comment, index) in allComments"
        v-bind:key="index"
      >
        <span class="comment__author">
          Autor:
          <strong>{{ comment.name }}</strong>
        </span>
        <p>{{ comment.message }}</p>

        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
      </div>
    </div>
  </div>
</template>

<script>
import FormComments from "./FormComments";
export default {
  components: {
    FormComments
  },
  data() {
    return {
      comments: []
    };
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },
  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name
      }));
    }
  },
  watch: {
    comments(value) {
      console.log("value", value);
    }
  }
};
</script>
