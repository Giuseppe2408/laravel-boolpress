<template>
  <div>
    <h1>Contact us</h1>
    <!-- @submit.prevent serve a non refreshare la pagina submitMessage è il nome del metodo-->
    <form @submit.prevent="submitMessage"> 
      <div class="mb-3">
        <label class="form-label" for="title">Name</label>
        <input class="form-control" type="text" name="name" id="name" v-model="name">       
      </div>     
      <div class="mb-3">
        <label class="form-label" for="title">Email</label>
        <input class="form-control" type="email" name="email" id="email" v-model="email">       
      </div>
      <div class="mb-3">
        <label class="form-label" for="title">Content</label>
        <textarea class="form-control"  name="content" id="content" v-model="content" cols="30" rows="10"></textarea>      
      </div> 
      <div>
        <input class="form-check-input" type="checkbox" name="newsletter" id="newsletter" v-model="mailingList">
        <label class="form-check-label" for="newsletter">Iscrivimi alla newsletter</label>
      </div>
      <button type="submit" class="btn btn-primary">Send</button>
    </form>
  </div>
</template>

<script>
export default {
    name: 'PageContacts',
    data(){
      return {
        name:        '',
        email:       '',
        content:     '',
        mailingList: true,
      }
    },


    // metodi di vue
    methods: {
      submitMessage() {
        axios.post('/api/mails/create', {
          name:         this.name,
          email:        this.email,
          content:      this.content,
          mailingList:  this.mailingList,
        })
        .then(res => console.log(res.data));
      }
    }
}
</script>

<style lang="scss" scoped>

</style>
