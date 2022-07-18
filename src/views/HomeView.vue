<template>
  <div class="home">
  
   <v-carousel cycle
    
     show-arrows-on-hover>  <template v-slot:prev="{ on, attrs }">
      <v-btn
        color="#FF7704"
        v-bind="attrs"
        v-on="on"
      >Previous</v-btn>
    </template>
    <template v-slot:next="{ on, attrs }">
      <v-btn
        color="#3f51b5"
        v-bind="attrs"
        v-on="on"
      >Next</v-btn>
    </template>
    <v-carousel-item
      v-for="film in filmovi" 
      :key="film.imdbID"
      
      reverse-transition="fade-transition"
      transition="fade-transition"
    > <v-card target="blank" :href="film.url">
            <v-img  
            style=" "
            :src="film.Poster"> 
            
    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title> {{ film.Title }}</v-list-item-title>

        <v-list-item-subtitle>
          {{film.Year }}
        </v-list-item-subtitle>

     
      </v-list-item-content>
    </v-list-item>
                 
    </v-img> </v-card>
    </v-carousel-item>
  </v-carousel>
  
      </div>
</template>


<script>
export default {
name: 'HomeView',
created() {this.dohvatiNajpopularnije()},

data() {
  return {
       filmovi:['Thor', 'Minions', 'Toronto', 'Batman'],
        slike: [],
      }},


methods: {dohvatiNajpopularnije: function() {
for(const film of this.filmovi){this.axios.get('https://www.omdbapi.com/?apikey=421c5dbb&y=2022&s=' + film).then((response) => {this.filmovi = response.data.Search})}}
}
     

}



</script>
