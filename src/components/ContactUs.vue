<template>
  <div>
    <v-divider></v-divider>
    <v-spacer></v-spacer>

    <v-container class="lighten-5 mb-6">
      <v-row style="padding-top: 150px;">
        <v-col>
          <v-card class="mx-auto" max-width="344" outlined>
            <v-card-title>Contact Details</v-card-title>

            <v-card-subtitle>
              <!-- <v-icon right>mdi-email</v-icon>Email Id: yadavmegha00@gmail.com 
              <v-icon right>mdi-phone</v-icon>-->
              <br />Tushar Salaskar : 9970011338
              <br />Satish Salaskar : 94225073
              <br />
              <b>Address :</b> Vimal Niwas, Ajinkya Colony, Behind Vaishali Hotel, Sr. No. 13,
              Opp. Akashawani , Hadpsar, Pune 411028
            </v-card-subtitle>
          </v-card>
        </v-col>
        <v-col>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-text-field v-model="name" :counter="10" :rules="nameRules" label="Name" required></v-text-field>

            <v-text-field v-model="email" :rules="emailRules" label="E-mail" required></v-text-field>

            <v-text-field v-model="contactNo" :rules="contactNoRules" label="Contact No." required></v-text-field>
            <v-text-field v-model="subject" label="Subject" required></v-text-field>

            <v-text-field v-model="message" label="Your Message" required></v-text-field>

            <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate">Submit</v-btn>

            <v-btn color="error" class="mr-4" @click="reset">Reset</v-btn>
          </v-form>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "ContactUs",
  data() {
    return {
      valid: true,
      name: "",
      nameRules: [
        v => !!v || "Name is required",
        v => (v && v.length <= 10) || "Name must be less than 10 characters"
      ],
      email: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+\..+/.test(v) || "E-mail must be valid"
      ],
      contactNoRules: [
        v => !!v || "Contact No is required",
        v => (v && v.length == 10) || "Contact No must be valid"
      ],
      contactNo: "",
      message: "",
      subject: ""
    };
  },
  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }
  }
};
</script>

<style>
</style>