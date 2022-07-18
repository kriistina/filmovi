<template>
  <div>
    <v-card class="mx-auto" dark max-width="1000" style="background-color:#1a1a1a">
      <v-card-title style="padding-top:50px ;">
        <span class="text-h1 font-weight-light">O filmu...</span>
      </v-card-title>

      <v-card-text class="text-h6 font-weight-bold">
        Kao i drugi oblici umjetnosti, film je namijenjen publici. Filmovi se
        gledaju u posebnom prostoru za projekciju (kino), ili bilo gdje drugdje
        (video). Film se često spominje kao sedma umjetnost, kao što je strip
        nazvan devetom umjetnošću. Filmsko djelo je cjelovit te društveno i
        doživljajno svrhovit filmski proizvod. Film i kinematografiju sustavno
        proučava humanističko-znanstvena disciplina filmologija.
      </v-card-text>
      <div>
        <v-textarea
          outlined
          label="Koji je vaš najdraži film?"
          placeholder="Ostavite svoj komentar..."
        ></v-textarea>
        <v-btn
          :loading="loading3"
          :disabled="loading3"
          color="#3f51b5"
          class="ma-2 white--text"
          @click="loader = 'loading3'"
        >
          Upload
          <v-icon right dark> mdi-cloud-upload </v-icon>
        </v-btn>
      </div>
    </v-card>
  </div>
</template>

<script>
export default {};
</script>
