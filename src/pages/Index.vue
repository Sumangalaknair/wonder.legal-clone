<template>
  <q-page class="flex">
    <div class="col left-side q-pa-md">
      <q-input
        outlined
        v-model="name"
        label="Enter the name of the recipient"
      />
      <br />

      <q-input outlined v-model="position" label="Enter the position" />
      <br />

      <q-input
        outlined
        v-model="companyName"
        label="Name of the organization"
      />
      <br />

      <q-input outlined v-model="startDate" label="The contract begins on" />
      <br />

      <q-input outlined v-model="months" label="Duration in months" />
      <br />

      <q-input outlined v-model="endDate" label="Ending date" /> <br />
    </div>

    <div class="col right-side q-pa-sm">
      <div class="text-center text-h5 text-weight-light">Document Preview</div>
      <br />
      <br />

      <div>
        <p>
          Dear <b>{{ name }}</b> <span v-if="name.length < 1">______</span> ,
          <br />

          We are delighted to offer you the position of <b>{{ position }}</b>
          <span v-if="position.length < 1">________</span> at out company,
          <b>{{ companyName }}</b>
          <span v-if="companyName.length < 1">________</span> starting from:
          <b>{{ startDate }}</b>
          <span v-if="startDate.length < 1">________</span> for a period of
          <b>{{ months }}</b>
          <span v-if="months.length < 1">________</span> months until
          <b>{{ endDate }}</b> <span v-if="endDate.length < 1">________</span>.
        </p>
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
      position: "",
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
