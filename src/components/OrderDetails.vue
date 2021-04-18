<template>
  <div>
    <v-divider></v-divider>

    <v-container class="lighten-5 mb-6">
      <v-row style="padding-top: 50px;">
        <v-col>
          <v-form>
            <h2>Order Mangoes</h2>
            <v-spacer></v-spacer>

            <v-autocomplete
              v-model="mangoType"
              :items="items"
              filled
              label="Mango Type"
              :rules="[v => !!v || 'Mango type is required']"
            ></v-autocomplete>
            <span>Select Size</span>

            <v-item-group mandatory v-model="grade">
              <v-container>
                <v-row>
                  <v-col v-for="n in grades" :key="n.size" cols="12" md="6">
                    <v-item v-slot="{ active, toggle }">
                      <v-card
                        class="d-flex align-center"
                        :color="active ? 'primary' : ''"
                        :class=" active ? 'rounded-card' : '' "
                        height="80"
                        @click="toggle"
                      >
                        <v-card-text class="headline font-weight-bold">
                          <v-list-item>
                            <v-col>
                              <span class="fontSize">Size : {{n.size}}</span>
                            </v-col>
                            <v-divider class="verticalDivider" vertical></v-divider>
                            <v-col>
                              <span class="fontSize">Rate : {{n.rate}}/Dz ({{n.avgSize}} gm avg.)</span>
                            </v-col>
                          </v-list-item>
                        </v-card-text>
                        <!-- 
                        <v-scroll-y-transition>
                          <div
                            v-if="active"
                            :color="active ? 'primary' : ''"
                            class="display-3 flex-grow-1 text-center"
                          >Active</div>
                        </v-scroll-y-transition>-->
                      </v-card>
                    </v-item>
                  </v-col>
                </v-row>
              </v-container>
            </v-item-group>
            <span class="subheading">Select Quantity</span>

            <v-chip-group
              v-model="selection"
              active-class="deep-purple--text text--accent-4"
              mandatory
            >
              <v-chip v-for="size in quantity" :key="size" :value="size">{{ size }}</v-chip>
            </v-chip-group>
          </v-form>
        </v-col>
        <v-col>
          <v-card class="mx-auto" max-width="360" outlined>
            <v-list-item three-line class="cardValues">
              <v-list-item-content>
                <v-list-item-title class="headline mb-1">Selected Order Details</v-list-item-title>
                <v-list-item-subtitle class="cardSubtitle">
                  <p>
                    Type : {{mangoType}}
                    <br />
                    Grade : {{grades[grade].size}} size ({{grades[grade].avgSize}} gm avg.)
                    <br />
                    quantity(In dozen) : {{selection}}
                  </p>
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>

            <v-card-actions>
              <!-- <v-btn outlined rounded text>Order Now</v-btn> -->
              <order-confirmation />
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import OrderConfirmation from "./OrderConfirmation.vue";
export default {
  name: "OrderDetails",
  components: {
    OrderConfirmation
  },
  data() {
    return {
      mangoType: "",
      items: ["Hapus", "Badami", "Payari"],
      grades: [
        { size: "A1+", rate: 100, avgSize: 300 },
        { size: "A1", rate: 100, avgSize: 250 },
        { size: "1", rate: 100, avgSize: 200 },
        { size: "2", rate: 100, avgSize: 100 }
      ],
      quantity: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"],
      selection: "1",
      grade: "0"
    };
  }
};
</script>

<style lang="scss" scoped>
.fontSize {
  font-size: 10px;
}
.verticalDivider {
  margin-top: 25px;
  margin-bottom: 25px;
}
.cardValues {
  min-height: 140px !important;
}
.cardSubtitle {
  overflow: initial !important;
}
</style>