<template>
  <div>
    <div>
      <!-- Table Search bar -->
      <v-text-field
        v-model="search"
        @change="dohvatiFilmApi()"
        append-icon="mdi-magnify"
        label="Search"
        solo
        style="margin: 10px"
        background-color="deep-purple"
        placeholder="Upisite film...."
      ></v-text-field>
      <h1 style="color: #ef6c00; padding-top: 50px">80s:</h1>
      <v-row class="mb-6" no-gutters>
        <v-col v-for="film in filmovi80" :key="film.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="film.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="film.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              film.title
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
                  {{ film.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ film.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ film.crew }}
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
        <v-col v-for="film in filmovi90" :key="film.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="film.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="film.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              film.title
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
                  {{ film.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ film.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ film.crew }}
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
        <v-col v-for="film in filmovi20" :key="film.id">
          <v-card
            style="background-color: #1a1a1a"
            :loading="loading"
            class="mx-auto my-12"
            max-width="374px"
            target="blank"
            :href="film.url"
          >
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <v-img height="250" :src="film.image"></v-img>

            <v-card-title class="indigo--text text--lighten-1">{{
              film.title
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
                  {{ film.imDbRating }}
                </div>
              </v-row>

              <div class="my-4 indigo--text text--lighten-1 text-subtitle-1">
                {{ film.year }}
              </div>

              <div class="indigo--text text--lighten-1">
                Stars:
                {{ film.crew }}
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
    filmovi80: [],
    filmovi90: [],
    filmovi20: [],
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
        .get("https://imdb-api.com/en/API/Top250Movies/k_ho8rs607")
        .then((response) => {
          const filmovi = response.data.items;
          for (const film of filmovi) {
            const godina = Number(film.year);

            if (1980 <= godina && godina < 1990 && this.filmovi80.length < 4) {
              this.filmovi80.push(film);
              console.log(godina);
            } else if (
              1990 <= godina &&
              godina < 2000 &&
              this.filmovi90.length < 4
            ) {
              this.filmovi90.push(film);
            } else if (
              2000 <= godina &&
              godina < 2030 &&
              this.filmovi20.length < 4
            ) {
              this.filmovi20.push(film);
            }
          }
        });
    },
  },
};
</script>
