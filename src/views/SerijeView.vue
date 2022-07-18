<template>
  <div>
    <div>
      <h1 style="color: #ef6c00; padding-top: 50px">80s:</h1>
      <v-row class="mb-6" no-gutters>
        <v-col v-for="serija in serije80" :key="serija.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="serija.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="serija.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              serija.title
            }}</v-card-title>

            <v-card-text>
              <v-row align="center" class="mx-0">
                <v-rating
                  :value="4.5"
                  background-color="orange darken-3"
                  color="orange"
                  dense
                  half-increments
                  readonly
                  size="14"
                ></v-rating>

                <div class="indigo--text text--lighten-1 ms-4">
                  {{ serija.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ serija.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ serija.crew }}
              </div>
            </v-card-text>

            <v-divider class="mx-4"></v-divider>

            <v-textarea
              
              dark
              label="Komentiraj"
              rows="1"
              prepend-icon="mdi-comment"
            ></v-textarea>

            <v-card-actions>
              <v-btn color="orange darken-3" text @click="reserve">
                Objavi
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <div>
      <h1 style="color: #ef6c00; padding-top: 50px">90s:</h1>
      <v-row class="mb-6" no-gutters>
        <v-col v-for="serija in serije90" :key="serija.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="serija.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="serija.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              serija.title
            }}</v-card-title>

            <v-card-text>
              <v-row align="center" class="mx-0">
                <v-rating
                  :value="4.5"
                  background-color="orange darken-3"
                  color="orange"
                  dense
                  half-increments
                  readonly
                  size="14"
                ></v-rating>

                <div class="indigo--text text--lighten-1 ms-4">
                  {{ serija.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ serija.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ serija.crew }}
              </div>
            </v-card-text>

            <v-divider class="mx-4"></v-divider>

            <v-textarea
              
              dark
              label="Komentiraj"
              rows="1"
              prepend-icon="mdi-comment"
            ></v-textarea>

            <v-card-actions>
              <v-btn color="orange darken-3" text @click="reserve">
                Objavi
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </div>

     <div>
      <h1 style="color: #ef6c00; padding-top: 50px">20s:</h1>
      <v-row class="mb-6" no-gutters>
        <v-col v-for="serija in serije20" :key="serija.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="serija.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="serija.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              serija.title
            }}</v-card-title>

            <v-card-text>
              <v-row align="center" class="mx-0">
                <v-rating
                  :value="4.5"
                  background-color="orange darken-3"
                  color="orange"
                  dense
                  half-increments
                  readonly
                  size="14"
                ></v-rating>

                <div class="indigo--text text--lighten-1 ms-4">
                  {{ serija.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ serija.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ serija.crew }}
              </div>
            </v-card-text>

            <v-divider class="mx-4"></v-divider>

            <v-textarea
              
              dark
              label="Komentiraj"
              rows="1"
              prepend-icon="mdi-comment"
            ></v-textarea>

            <v-card-actions>
              <v-btn color="orange darken-3" text @click="reserve">
                Objavi
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </div>

  </div>
</template>

<script>
export default {
  created() {
    this.dohvatiFilmApi();
  },
  data: () => ({
    serije80: [],
    serije90: [],
    serije20: [],
    loading: false,
    selection: 1,
  }),

  methods: {
    reserve() {
      this.loading = true;

      setTimeout(() => (this.loading = false), 2000);
    },
    dohvatiFilmApi: function () {
      this.axios
        .get("https://imdb-api.com/en/API/Top250TVs/k_ho8rs607")
        .then((response) => {
          const serije = response.data.items;
          for (const serija of serije) {
            const godina = Number(serija.year);

            if (1980 <= godina && godina < 1990 && this.serije80.length < 4) {
              this.serije80.push(serija);
              console.log(godina);
            } else if (
              1990 <= godina &&
              godina < 2000 &&
              this.serije90.length < 4
            ) {
              this.serije90.push(serija);
            } else if (
              2000 <= godina &&
              godina < 2030 &&
              this.serije20.length < 4
            ) {
              this.serije20.push(serija);
            }
          }
        });
    },
  },
};
</script>
