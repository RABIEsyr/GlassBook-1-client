<template>
  <v-layout row wrap align-center>
    <v-flex xs12 sm10 md9 lg6 xlg6 offset-md2>
      <div>
        <v-card class="my-3" hover>
          <v-img height="350px" :src="image" alt="no image"></v-img>
          <v-container fill-height fluid>
            <v-layout>
              <v-flex xs12 align-end d-flex>
                <span class="headline"> {{ text }} </span>
              </v-flex>
            </v-layout>
          </v-container>
          <v-card-text> description </v-card-text>
          <v-card-actions>
            <!-- <v-chip small color="secondary" class="white--text">
                    article.source.name
                  </v-chip> -->
            <!--  -->

            <v-row style="padding: 10px">
              <v-dialog v-model="dialog" persistent max-width="600px">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn color="primary" dark v-bind="attrs" v-on="on">
                    Commnet
                  </v-btn>
                </template>
                <v-card>
                  <v-card-title>
                    <span class="headline">comment</span>
                  </v-card-title>
                  <v-card-text>
                    <v-container>
                      <v-row>

                        <v-col cols="12" >
                          <v-text-field
                            label="leave comment"
                            required
                            v-model="comment"
                          ></v-text-field>
                        </v-col>
                       
                      </v-row>
                    </v-container>
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="dialog = false">
                      Close
                    </v-btn>
                    <v-btn color="blue darken-1" text @click="dialog = false">
                      Save
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
            <!--  -->
            <v-spacer></v-spacer>
            <v-btn icon class="red--text">
              <v-icon small>fa-reddit</v-icon>
            </v-btn>
            <v-btn icon class="light-blue--text">
              <v-icon small>fa-twitter</v-icon>
            </v-btn>
            <v-btn icon class="blue--text text--darken-4">
              <v-icon small>fa-facebook</v-icon>
            </v-btn>
            <v-btn icon class="red--text">
              <v-icon small>fa-google-plus</v-icon>
            </v-btn>
            <v-btn icon class="blue--text text--darken-4">
              <v-icon small>fa-linkedin</v-icon>
            </v-btn>
            <v-spacer></v-spacer>

            <v-btn small replace color="info" href="'image.url'" target="_blank"
              >Read More</v-btn
            >
          </v-card-actions>
        </v-card>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  props: {
    text: String,
    image: String,
  },
  data() {
    return {
      dialog: false,
      comment: ''
    };
  },
};
</script>

<style scoped>
</style>