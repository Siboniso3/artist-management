<template>
    <div class="container">
        <h1 >Event Organizer view</h1>
        <h1 class ="text-center">Artist list</h1>
        <table class="table table-striped">
         <thead>
         <th>Artist Id</th>
         <th>Artist First Name</th>
          <th>Artist Last Name</th>
         <th>Stage Name</th>
         <th>Genre</th>
         <!-- <th>Location</th> -->
         <!-- <th>Booking Status</th>  -->
        </thead>
        <tbody>
            <tr v-for="artist in artists" v-bind:key="artist.id">
                <td>{{artist.id}}</td>
                <td>{{artist.fName}}</td>
                <td>{{artist.lName}}</td>
                <td>{{artist.stageName}}</td>
                <td>{{artist.genre}}</td>
                <!-- <td>{{artist.location}}</td> -->
                <!-- <td>{{artist.status}}</td> -->
            </tr>
        </tbody>

        </table>
    </div>
</template>

<script>
import ArtistService from '../assets/services/ArtistService'
 

export default{
    name :'Artists-list',
    data(){
        return{
         artists : []
        }
      
    },
    methods:{
     getArtists(){
       ArtistService.getArtists().then((response) =>{
        this.artists =response.data
       });
     }
    },
    created(){
     this.getArtists()
    }

}
</script>
<style>
 .container>div, h1 {
  flex: 1;
}
</style>