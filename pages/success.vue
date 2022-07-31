<template>
  <div>
    <section class="relative pt-20 pb-32 2xl:py-40 bg-gray-800 overflow-hidden">
      <div
        class="absolute bottom-0 inset-x-0 h-full bg-gradient-zospace-1"
      ></div>
      <div
        class="
          absolute
          bottom-0
          inset-x-0
          h-3/5
          w-2full
          -ml-64
          -mb-12
          bg-gradient-zospace-2
          transform
          -rotate-6
        "
      ></div>
      <div class="relative container px-3 mx-auto">
        <div class="max-w-3xl mx-auto text-center">
          <span
            class="
              text-lg
              font-bold
              text-transparent
              bg-clip-text bg-gradient-to-br
              from-yellow-200
              to-orange-600
            "
            >SUCCESSFUL!!!!</span
          >
          <h2
            class="my-10 text-3xl lg:text-6xl font-bold font-heading text-white"
          >
            Click on the Button Bellow to Confirm Payment
          </h2>
          <div class="max-w-md mx-auto">
            <button
              @click="verifyPayment"
              class="
                inline-block
                mb-4
                sm:mb-0 sm:mr-4
                py-4
                px-12
                text-white
                font-bold
                bg-blue-500
                hover:bg-blue-600
                rounded-full
                transition
                duration-200
              "
              href="#"
            >
              Verify
            </button>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Swal from "sweetalert2";
export default {
  data() {
    return {};
  },
  methods: {
    verifyPayment() {
      const id = JSON.parse(localStorage.getItem("id"));
      var axios = require("axios");

      var config = {
        method: "get",
        url: `https://api.stripe.com/v1/checkout/sessions/${id}`,
        headers: {
          Authorization:
            "Bearer  sk_test_51LIEnMDw37K7KqJsgA0MLKcjUNYnca6j2Fn4VseXUsSaQstpdWUloKZN75KT0Ia4aD48D1h9nMfxyUg36xtbQynz00LyjMYwbk",
        },
      };

      axios(config)
        .then(function (response) {
          console.log(JSON.stringify(response.data));
          if (response.data.payment_status == "paid") {
            Swal.fire({
              position: "top-end",
              icon: "success",
              title: "Payment was Successful",
              showConfirmButton: false,
              timer: 3000,
            });
          } else {
            Swal.fire({
              icon: "error",
              title: "Oops...",
              text: "Payment was not made",
            });
          }
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>