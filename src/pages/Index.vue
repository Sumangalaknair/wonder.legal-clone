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
    <div id="loader-bg" v-if="show" class="preloader">
      <div id="pulse-loader">
        <div class="pulse-loader-1"></div>
        <div class="pulse-loader-2"></div>
      </div>
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
          <span v-if="position.length < 1">________</span> at our company,
          <b>{{ companyName }}</b>
          <span v-if="companyName.length < 1">________</span> starting from
          <b>{{ startDate }}</b>
          <span v-if="startDate.length < 1">________</span> for a period of
          <b>{{ months }}</b>
          <span v-if="months.length < 1">________</span> months until
          <b>{{ endDate }}</b> <span v-if="endDate.length < 1">________</span>.
        </p>
      </div>

      <br />
      <q-btn
        color="primary"
        @click="createPDF"
        icon="get_app"
        label="Download PDF"
      />
    </div>
    <!-- end col -->
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
      companyName: "",
      show: true,
    };
  },
  methods: {
    createPDF() {
      let pdfName = "offer-letter";
      var lMargin = 15; //left margin in mm
      var rMargin = 15; //right margin in mm
      var pdfInMM = 210; // width of A4 in mm
      var pageCenter = pdfInMM / 2;
      var pageleft = 20;

      var doc = new jsPDF("p", "mm", "a4");
      var paragraph = `Dear ${this.name},\nWe are delighted to offer you the position of ${this.position} at our company, ${this.companyName} starting from ${this.startDate} for a period of ${this.months} until ${this.endDate}`;

      var lines = doc.splitTextToSize(paragraph, pdfInMM - lMargin - rMargin);
      doc.setLineHeightFactor(1.5);
      doc.text("OFFER LETTER", pageCenter, 20, "center");
      doc.text(lines, pageleft, 40, "left"); //see this line
      doc.save(pdfName + ".pdf");
    },

    showToggle() {
      setTimeout(() => {
        this.show = false;
      }, 2000);
    },
  },
  mounted() {
    if (Boolean(this.show)) this.showToggle();
  },
};
</script>

<style lang="scss">
.left-side {
  background-color: $cyan-2;
}
p {
  font-size: 18px;
}
#pulse-loader .pulse-loader-1,
#pulse-loader .pulse-loader-2 {
  -webkit-border-radius: 1000px;
  -moz-border-radius: 1000px;
  -o-border-radius: 1000px;
  border-radius: 1000px
}

#pulse-loader {
  position: fixed;
  z-index: 20;
  left: 50%;
  top: 50%;
  width: 300px;
  height: 300px;
  margin-left: -150px;
  margin-top: -150px
}

#pulse-loader {
  top: 45%
}

#pulse-loader>div {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-width: 20px;
  border-style: solid;
  border-color: rgb(255, 235, 57)
}

#pulse-loader .pulse-loader-1 {
  -webkit-animation: pulse1 1s .5s ease infinite;
  -moz-animation: pulse1 1s .5s ease infinite;
  -ms-animation: pulse1 1s .5s ease infinite;
  -o-animation: pulse1 1s .5s ease infinite;
  animation: pulse1 1s .5s ease infinite
}

#pulse-loader .pulse-loader-2 {
  -webkit-animation: pulse1 1s ease infinite;
  -moz-animation: pulse1 1s ease infinite;
  -ms-animation: pulse1 1s ease infinite;
  -o-animation: pulse1 1s ease infinite;
  animation: pulse1 1s ease infinite
}

@-webkit-keyframes pulse1 {
  0% {
    -webkit-transform: scale(0)
  }
  40% {
    -webkit-transform: scale(0.3);
    opacity: 1
  }
  100% {
    -webkit-transform: scale(1);
    opacity: 0
  }
}

@-moz-keyframes pulse1 {
  0% {
    -moz-transform: scale(0)
  }
  40% {
    -moz-transform: scale(0.3);
    opacity: 1
  }
  100% {
    -moz-transform: scale(1);
    opacity: 0
  }
}

@-o-keyframes pulse1 {
  0% {
    -o-transform: scale(0)
  }
  40% {
    -o-transform: scale(0.3);
    opacity: 1
  }
  100% {
    -o-transform: scale(1);
    opacity: 0
  }
}

@-ms-keyframes pulse1 {
  0% {
    -ms-transform: scale(0)
  }
  40% {
    -ms-transform: scale(0.3);
    opacity: 1
  }
  100% {
    -ms-transform: scale(1);
    opacity: 0
  }
}

@keyframes pulse1 {
  0% {
    transform: scale(0)
  }
  40% {
    transform: scale(0.3);
    opacity: 1
  }
  100% {
    transform: scale(1);
    opacity: 0
  }
}
</style>