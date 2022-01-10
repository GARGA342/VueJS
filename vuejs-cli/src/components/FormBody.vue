<template>
  <form>
      <div class="form-group">
        <label for="name">Name</label>
        <input
          v-model="name"
          type="text"
          class="form-control"
          id="name"
          aria-describedby="nameHelp"
        />
        <small id="nameHelp" class="form-text text-muted"
          >If you don't enter this field, your comment will be anonymous.</small
        >
      </div>
      <div class="form-group">
        <label for="email">Email</label>
        <input v-model="email" type="email" class="form-control" id="email" />
      </div>
      <div class="form-group">
        <label for="text">Text</label>
        <textarea v-model="text" id="text" class="form-control"></textarea>
      </div>
      <button type="submit" class="btn btn-primary" v-on:click.prevent="register">
        Register
      </button>
    </form>
    
    <!-- The list was here! -->
</template>

<script>
   export default {
       data(){
           return{
               name: '',
               email: '',
               text: ''
           }
       },
       methods: {
          register() {
            if (this.email.trim() === "" || this.text.trim() === "") {
              return alert('The fields "email" and "text" must be filled!');
            } else {
                      
              this.$emit('emit_value', {
                name: this.name,
                email: this.email,
                text: this.text
              })

              this.name = "";
              this.email = "";
              this.text = "";
            }
          }
        }
   }
</script>