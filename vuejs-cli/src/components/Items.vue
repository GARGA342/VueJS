<template>
  <div class="app">
    <div class="container mt-5">
      <h1><strong>Form Content</strong></h1>
      <hr />
      <!-- The form was here! -->
      <FormBody v-on:emit_value="getData"></FormBody>
    </div>

    <!-- Success message
    <div class="alert alert-success" role="alert">
      Successfully registered!
    </div> -->

    <div class="container mt-5" style="position: relative;">
      <div class="list-group list-group-item mt-5" v-if="items.length <= 0">
        <small class="form-text text-muted">No comments yet!</small>
      </div>
      <div class="form-group mt-5">
        <div class="list-group-item" v-for="(item, index) in allItems" :key="index">
          <span><strong>Name: </strong>{{ item.name }}</span
          ><br />
          <span><strong>Email: </strong>{{ item.email }}</span
          ><br />
          <p>
            <span><strong>Text: </strong>{{ item.text }}</span>
          </p>
          <div>
            <a href="#" v-on:click.prevent="remove(index)">Delete</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import FormBody from './FormBody'
  export default {
    components: {
      FormBody
    },
    data() {
      return {
          items: []
      }
    },
    methods: {
      getData(item){
        this.items.push(item)
        //document.getElementById('success_message').classList.toggle('fade')
      },
      remove(index) {
        this.items.splice(index, 1)
      }
    },
    computed: {
      allItems() {
        return this.items.map((item) => ({
          ...item,
          name: item.name.trim() === "" ? "anonymous" : item.name,
        }));
      },
    },
    watch: {
      items(val) {
        console.log("value", val);
      },
    }
 }
</script>

<style></style>