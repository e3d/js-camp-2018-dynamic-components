<template>
  <section class="markup-demo-container section">
   <radio-group :options="options" v-model="activeView"></radio-group>
    <br/>
    <section class="markup-demo-wrap card">     
      <comment>
Notice how there are no additional elements introduced around `component` 
or the child it is rendering.
      </comment>
      <component :is="activeView" v-model="contact" class="card-content">
      </component>
    </section>
  </section>    
</template>

<script>
// @ is an alias to /src

export default {
  name: "MarkupDemo",
  comments: true,
  components: {
    ContactDetails: () => import("@/components/ContactDetails"),
    AddressDetails: () => import("@/components/AddressDetails"),
    RadioGroup: () => import("@/components/FormControls/RadioGroup")
  },
  data() {
    return {
      options: ["ContactDetails", "AddressDetails"],
      activeView: "ContactDetails",
      contact: {
        firstName: "Evan",
        lastName: "Schultz",
        password: "iwantmymoney",
        email: "evan@",
        userName: "e-schultz",
        street1: "19 York Street",
        street2: "6th Floor",
        country: "Canada",
        postalCode: "N1N 2N2",
        province: "Ontario"
      }
    };
  }
};
</script>
<style>
.markup-demo-wrap {
  border: 1px solid black;
}
</style>
