<template>
  <q-page class="flex">
    <div class="col left-side q-pa-md">
      <q-scroll-area class="fit">
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
      </q-scroll-area>
    </div>

    <div class="col right-side q-pa-md">
      <div class="text-center text-h5 text-weight-regular">
        Document Preview
      </div>
      <q-separator />
      <br />
      <br />

      <div class="document">
        <div class="text-h5 text-center text-weight-light">OFFER LETTER</div>
        <br />
        <br />
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

      <br />
      <q-btn color="primary" @click="createPDF" icon="get_app" label="Download PDF" />
    </div>
    <!-- end col -->

    {{ paragraph }}
  </q-page>
</template>

<script>
import { jsPDF } from "jspdf";

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
  },
  methods: {
  createPDF () {
    let pdfName = 'offer-letter'; 
    var doc = new jsPDF();
    doc.text("OFFER LETTER", 85, 20);
    doc.save(pdfName + '.pdf');
  }
}
};
</script>

<style lang="scss">
.left-side {
  background-color: $cyan-2;
}
</style>
