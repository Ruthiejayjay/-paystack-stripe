<template>
  <div>
    <header class="bg-gray-900 sm:flex sm:justify-between sm:px-4 sm:py-3">
      <div class="flex items-center justify-between px-4 py-3 sm:0">
        <a
          class="
            flex
            title-font
            font-medium
            items-center
            text-white
            mb-4
            md:mb-0
          "
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            class="w-10 h-10 text-white p-2 bg-indigo-500 rounded-full"
            viewBox="0 0 24 24"
          >
            <path
              d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"
            ></path>
          </svg>
          <span class="ml-3 text-xl">Tailblocks</span>
        </a>

        <div class="sm:hidden">
          <button
            v-on:click="isOpen = !isOpen"
            type="button"
            class="focus:text-white focus:outline-none"
          >
            <img v-if="isOpen" src="~/assets/close.png" class="h-5 w-5" />
            <img v-if="!isOpen" src="~/assets/menu.svg" />
          </button>
        </div>
      </div>
      <div :class="isOpen ? 'block' : 'hidden'" class="px-2 pt-2 pb-4 sm:flex">
        <NuxtLink
          to="/"
          href="#"
          class="
            block
            px-2
            py-1
            text-white
            font-semibold
            rounded
            hover:bg-gray-800
          "
          >Home</NuxtLink
        >
        <a
          href="#"
          class="
            mt-1
            block
            px-2
            py-1
            text-white
            font-semibold
            rounded
            hover:bg-gray-800
            sm:mt-0 sm:ml-2
          "
          >Products</a
        >
        <button
          @click="verifyPaymentPaystack"
          class="
            mt-1
            block
            px-2
            py-1
            text-white
            font-semibold
            rounded
            hover:bg-gray-800
            sm:mt-0 sm:ml-2
          "
        >
          Verify
        </button>
      </div>
    </header>
  </div>
</template>

<script>
import Swal from "sweetalert2";
export default {
  data() {
    return {
      isOpen: false,
    };
  },

  methods: {
    verifyPaymentPaystack() {
      const reference = JSON.parse(localStorage.getItem("reference"));
      var axios = require("axios");

      var config = {
        method: "get",
        url: `https://api.paystack.co/transaction/verify/${reference}`,
        headers: {
          Authorization:
            "Bearer sk_test_0eb87185b90ad5bc1b42ef632afdb67837333bfa",
          Cookie:
            "sails.sid=s%3Aso4WnEXCGVdsN1GO0Cr8rjXSUH5gOzr6.sMTz6avZFJrrUtusLIF1hyyzwd3oF%2FRUzaqwi%2Fm%2F5Is",
        },
      };

      axios(config)
        .then(function (response) {
          
          if(response.data.data.status == "success") {
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