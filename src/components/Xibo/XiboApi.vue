<template>
  <button v-on:click="openUploadModal != openUploadModal" class="text-white p-2 bg-green-500 rounded" >Upload</button>
  <div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(){
    return {
      access_token: '',
      openUploadModal: false,

    }
  },
  mounted() {

    this.Authenticate();
    // this.getAllLibraryItems();

  },
  methods: {
    async Authenticate()
    {
      let credentials = new FormData();
      credentials.append('client_id', 'rEzZx6JD5OWTfwrywHjjqoG4J09kAJwnOJozucFf');
      credentials.append('client_secret', 'nEj4UaG7Z5dbl5o6l5esHslmfgvIXA7ZXJDpo9umOrJkhPUGeij9qLjTi74maNRqxsvFBjORrqrobr1GwvfNts5keJYhxdP26zs6EmRxfPa7taC2XXekUg6halwu2pWVL7QKfA5sjy9xwEJ55jXkSC1xFYRB1vCFXoU5C2uySP2xnZwlD8WVe8ksMV74Gc5zHXDn21Tt261FYKAneJowfougXp8rjNP27wfDWjjvQvA6rBQfuJ7XR05v1lWxvY')
      credentials.append('grant_type', 'client_credentials');
      await axios({
        method: 'post',
        url: 'http://192.168.178.82/api/authorize/access_token',
        data: credentials,
        headers: { 'Content-Type': 'multipart/form-data'  },
      }).then((response) => {
        this.access_token = response.data.access_token;
        if (this.access_token){

          this.getAllLibraryItems()

        }else{

          console.log("empty access token");

        }

        console.log('Bearer ' + this.access_token);
      }).catch((error) => {
        console.log(error)
      })
    },
    getAllLibraryItems()
    {
      axios({
        method: 'GET',
        url: 'http://192.168.178.82/api/library',
        mode: 'no-cors',
        headers: {
          'Authorization': 'Bearer XtDVSpCe9w35SZbpmALL7UrW0JVXY1aQ4twgsB0O',
          'Content-Type': 'application/json'
        }
      })
       .then((response) => {
          console.log(response)
       })
       .catch((response) => {
         console.log(response)
       })
    }
  }
}
</script>