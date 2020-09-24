<template>
  <q-page class="flex">
    <div class="col left-side q-pa-md">
      <q-input
        outlined
        v-model="name"
        label="Enter the name of the recipient"
      />
      <br />

      <q-input outlined v-model="companyName" label="Name of the organization" />
      <br />

      <q-input outlined v-model="startDate" label="The contract begins on" />
      <br />

      <q-input outlined v-model="months" label="Duration in months" />
      <br />

      <q-input outlined v-model="endDate" label="Ending date" /> <br />
    </div>

    <div class="col right-side q-pa-sm">
      <div class="text-center text-h5 text-weight-light">Document Preview</div> <br>

      <div>
        <p>Dear <b>{{ name }}</b>, <br> We are delighted to offer you the position of Software Developer at out company, <b>{{ companyName }}</b> starting from: <b>{{startDate}}</b> for a period of <b>{{ months }}</b> months until <b>{{ endDate }}</b>.</p>
      </div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      name: "",
      startDate: "",
      months: "",
      endDate: "",
      companyName: ""
    };
  }
};
</script>

<style lang="scss">
.right-side {
  background-color: $cyan-2;
}
</style>
