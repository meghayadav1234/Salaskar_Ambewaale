<template>
  <v-col cols="auto">
    <v-dialog transition="dialog-bottom-transition" max-width="600" v-model="dialog">
      <template v-slot:activator="{ on, attrs }">
        <v-btn color="primary" v-bind="attrs" v-on="on">Order Now</v-btn>
      </template>
      <template>
        <v-form ref="form" lazy-validation>
          <v-card>
            <v-toolbar color="primary" dark>Order Confirmation</v-toolbar>
            <v-card-text>
              <v-text-field
                v-model="fullName"
                :counter="10"
                :rules="nameRules"
                label="Name"
                required
              ></v-text-field>
              <v-text-field
                v-model="contactNumber"
                :rules="contactNoRules"
                label="Contact No."
                required
              ></v-text-field>
              <v-progress-linear
                color="blue"
                rounded
                height="6"
                :active="loading"
                :indeterminate="loading"
              ></v-progress-linear>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-btn text @click="validateForm">Submit</v-btn>
            </v-card-actions>
          </v-card>
        </v-form>
      </template>

      <!-- <v-card v-if="validForm && this.contactNumber && this.fullName" color="primary" dark>
        <v-card-text>
          Please stand by
          <v-progress-linear indeterminate color="white" class="mb-0"></v-progress-linear>
        </v-card-text>
      </v-card>-->
    </v-dialog>
  </v-col>
</template>

<script>
export default {
  name: "OrderConfirmation",
  data() {
    return {
      validForm: true,
      dialog: false,
      fullName: "",
      nameRules: [
        v => !!v || "Name is required",
        v => (v && v.length <= 10) || "Name must be less than 10 characters"
      ],
      contactNoRules: [
        v => !!v || "Contact No is required",
        v => (v && v.length == 10) || "Contact No must be valid"
      ],
      contactNumber: "",
      loading: false
    };
  },
  methods: {
    validateForm() {
      this.validForm = this.$refs.form.validate();
      if (this.validForm) {
        console.log("save data");
        //this.dialog = false;
        this.loading = true;
      }
    }
  }
};
</script>

<style>
</style>