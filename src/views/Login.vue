<template>
  <v-container fluid style="width: 50%">
    <br />
    <v-row>
      <v-col cols="12">
        <v-card height="auto">
          <v-row justify="center"> Prijavite se sa svojim računom. </v-row>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-col cols="12">
              <v-text-field
                solo
                outlined
                v-model="username"
                :rules="nameRules"
                label="Korisničko ime"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                solo
                outlined
                v-model="password"
                :type="show1 ? 'text' : 'password'"
                :rules="passwordRules"
                label="Lozinka"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-btn @click="validate(); submit(); loginAlert = true" :disabled="!valid">Login</v-btn>
            </v-col>
          </v-form>
        </v-card>
        <br />


        <v-col>
          <v-card height="auto">
            <v-row justify="center"> Nemate račun? </v-row>
            <v-row justify="center">
              <v-dialog v-model="dialog" persistent max-width="600px">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    color="light-blue darken-3"
                    dark
                    v-bind="attrs"
                    v-on="on"
                  >
                    Registrirajte se
                  </v-btn>
                </template>
                <v-card>
                  <v-card-title>
                    <span class="text-h5">Korisnički Profil</span>
                  </v-card-title>
                  <v-card-text>
                    <v-container>
                      <v-row>
                        <v-col cols="12">
                          <v-text-field
                            label="Korisničko ime*"
                            required
                          ></v-text-field>
                        </v-col>
                        <v-col cols="12">
                          <v-text-field label="Email*" required></v-text-field>
                        </v-col>
                        <v-col cols="12">
                          <v-text-field
                            label="Lozinka*"
                            type="password"
                            required
                          ></v-text-field>
                        </v-col>
                        <v-col cols="12" sm="6">
                          <v-select
                            :items="['0-17', '18-29', '30-54', '54+']"
                            label="Godine*"
                            required
                          ></v-select>
                        </v-col>
                        <v-col cols="12" sm="6">
                          <v-autocomplete
                            :items="[
                              'Akcija',
                              'Animirani',
                              'Komedija',
                              'Kriminalistički',
                              'Drama',
                              'Triler',
                              'Sitcom',
                              'Fantazija',
                              'Romantični',
                              'Science-fiction',
                              'Supernatural',
                              'Horor',
                            ]"
                            label="Žanrovi"
                            multiple
                          ></v-autocomplete>
                        </v-col>
                      </v-row>
                    </v-container>
                    <small>*obavezno polje</small>
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="dialog = false">
                      Zatvori
                    </v-btn>
                    <v-btn
                      color="blue darken-1"
                      text
                      @click="
                        dialog = false;
                        registerSuccess = true;
                      "
                    >
                      Spremi
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
            <v-row justify="center">
              <v-alert
                dense
                type="success"
                dismissible
                v-model="registerSuccess"
                >Uspješno ste kreirali račun!</v-alert
              >
            </v-row>
          </v-card>
        </v-col>
      </v-col>
    </v-row>
  </v-container>
</template>


<script>
export default {
  data() {
    return {
      show1: false,
      username: "",
      password: "",
      valid: true,
      registerSuccess: false,
      dialog: false,
      loginAlert: false,
      nameRules: [(v) => !!v || "Korisničko ime je potrebno!"],
      passwordRules: [(v) => !!v || "Lozinka je potrebna!"],
    };
  },

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    submit(){
      if(this.$refs.form.validate()){
        console.log(this.username)
      }
    }
  },
};
</script>
