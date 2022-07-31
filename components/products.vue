<template>
  <div>
    <section class="text-gray-400 bg-gray-900 body-font">
      <div class="container px-5 py-24 mx-auto">
        <div class="text-center text-3xl mb-2">
          <h1 class="font-bold text-white">Products List</h1>
        </div>
        <div class="flex flex-wrap -m-1">
          <div class="lg:w-1/4 md:w-1/2 p-4 w-full">
            <div class="block relative h-48 rounded overflow-hidden">
              <img
                alt="ecommerce"
                class="object-cover object-center w-full h-full block"
                src="~/assets/meatballs.jpg"
              />
            </div>
            <div class="mt-4">
              <h3
                class="
                  text-gray-500 text-xs
                  tracking-widest
                  font-bold
                  mb-1
                  uppercase
                "
              >
                stripe
              </h3>
              <h2 class="text-white title-font text-lg font-medium">
                Meat Balls
              </h2>
              <p class="mx-px">₦500.00</p>
              <div class="mb-2">
                <label for="">Quantity: </label>
                <input
                  type="number"
                  class="mb-1 bg-gray-800"
                  v-model="meatQuantity"
                />
              </div>
              <button
                @click="meatballs"
                class="
                  px-6
                  py-2
                  mt-2
                  font-semibold
                  cursor-pointer
                  text-center
                  focus:outline-none
                  transition
                  hover:shadow-lg
                  shadow
                  hover:bg-indigo-700
                  rounded
                  text-white
                  bg-indigo-600
                "
              >
                Buy
              </button>
            </div>
          </div>
          <div class="lg:w-1/4 md:w-1/2 p-4 w-full">
            <div class="block relative h-48 rounded overflow-hidden">
              <img
                alt="ecommerce"
                class="object-cover object-center w-full h-full block"
                src="~/assets/donut.jpg"
              />
            </div>
            <div class="mt-4">
              <h3
                class="
                  text-gray-500 text-xs
                  tracking-widest
                  font-bold
                  mb-1
                  uppercase
                "
              >
                stripe
              </h3>
              <h2 class="text-white title-font text-lg font-medium">Donuts</h2>
              <p class="mt-1">₦300.00</p>
              <div class="mb-2">
                <label for="">Quantity: </label>
                <input
                  type="number"
                  class="mb-1 bg-gray-800"
                  v-model="donutQuantity"
                />
              </div>

              <button
                @click="donut"
                class="
                  px-6
                  py-2
                  mt-2
                  font-semibold
                  cursor-pointer
                  text-center
                  focus:outline-none
                  transition
                  hover:shadow-lg
                  shadow
                  hover:bg-indigo-700
                  rounded
                  text-white
                  bg-indigo-600
                "
              >
                Buy
              </button>
            </div>
          </div>
          <div class="lg:w-1/4 md:w-1/2 p-4 w-full">
            <div class="block relative h-48 rounded overflow-hidden">
              <img
                alt="ecommerce"
                class="object-cover object-center w-full h-full block"
                src="~/assets/pancake.jpg"
              />
            </div>
            <div class="mt-4">
              <h3
                class="
                  text-gray-500 text-xs
                  tracking-widest
                  font-bold
                  mb-1
                  uppercase
                "
              >
                paystack
              </h3>
              <h2 class="text-white title-font text-lg font-medium">
                Pancakes
              </h2>
              <div class="mb-2">
                <label for="">Email: </label>
                <input
                  type="email"
                  class="mb-1 bg-gray-800"
                  v-model="pancakeEmail"
                />
              </div>
              <div class="mb-2">
                <label for="">Amount: </label>
                <input
                  type="number"
                  class="mb-1 bg-gray-800"
                  v-model="pancakeAmount"
                />
              </div>
              <button
                @click="pancake"
                class="
                  px-6
                  py-2
                  mt-2
                  font-semibold
                  cursor-pointer
                  text-center
                  focus:outline-none
                  transition
                  hover:shadow-lg
                  shadow
                  hover:bg-indigo-700
                  rounded
                  text-white
                  bg-indigo-600
                "
              >
                Buy
              </button>
            </div>
          </div>
          <div class="lg:w-1/4 md:w-1/2 p-4 w-full">
            <div class="block relative h-48 rounded overflow-hidden">
              <img
                alt="ecommerce"
                class="object-cover object-center w-full h-full block"
                src="~/assets/pizza.jpg"
              />
            </div>
            <div class="mt-4">
              <h3
                class="
                  text-gray-500 text-xs
                  tracking-widest
                  font-bold
                  mb-1
                  uppercase
                "
              >
                paystack
              </h3>
              <h2 class="text-white title-font text-lg font-medium">Pizza</h2>
              <div class="mb-2">
                <label for="">Email: </label>
                <input type="email" class="mb-1 bg-gray-800" v-model="email" />
              </div>
              <div class="mb-2">
                <label for="">Amount: </label>
                <input
                  type="number"
                  class="mb-1 bg-gray-800"
                  v-model="amount"
                />
              </div>
              <button
                @click="pizza"
                class="
                  px-6
                  py-2
                  mt-2
                  font-semibold
                  cursor-pointer
                  text-center
                  focus:outline-none
                  transition
                  hover:shadow-lg
                  shadow
                  hover:bg-indigo-700
                  rounded
                  text-white
                  bg-indigo-600
                "
              >
                Buy
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      amount: "",
      pancakeEmail: "",
      pancakeAmount: "",
      meatQuantity: "",
      donutQuantity: "",
    };
  },

  methods: {
    //stripe intialization
    meatballs() {
      var axios = require("axios");
      var qs = require("qs");
      var data = qs.stringify({
        mode: "subscription",
        "line_items[0][price]": "price_1LP9dlDw37K7KqJs8FEvjh9l",
        "line_items[0][quantity]": this.meatQuantity,
        cancel_url: "http://localhost:3000/cancel",
        success_url: "http://localhost:3000/success",
      });
      var config = {
        method: "post",
        url: "https://api.stripe.com/v1/checkout/sessions",
        headers: {
          "Content-Type": "application/x-www-form-urlencoded",
          Authorization:
            "Bearer  sk_test_51LIEnMDw37K7KqJsgA0MLKcjUNYnca6j2Fn4VseXUsSaQstpdWUloKZN75KT0Ia4aD48D1h9nMfxyUg36xtbQynz00LyjMYwbk",
        },
        data: data,
      };

      axios(config)
        .then(function (response) {
          localStorage.setItem("id", JSON.stringify(response.data.id));
          window.location.href = response.data.url;
        })
        .catch(function (error) {
          console.log(error);
        });
    },

    donut() {
      var axios = require("axios");
      var qs = require("qs");
      var data = qs.stringify({
        mode: "subscription",
        "line_items[0][price]": "price_1LPLdADw37K7KqJsAVQM8Yv2",
        "line_items[0][quantity]": this.donutQuantity,
        cancel_url: "http://localhost:3000/cancel",
        success_url: "http://localhost:3000/success",
      });
      var config = {
        method: "post",
        url: "https://api.stripe.com/v1/checkout/sessions",
        headers: {
          "Content-Type": "application/x-www-form-urlencoded",
          Authorization:
            "Bearer  sk_test_51LIEnMDw37K7KqJsgA0MLKcjUNYnca6j2Fn4VseXUsSaQstpdWUloKZN75KT0Ia4aD48D1h9nMfxyUg36xtbQynz00LyjMYwbk",
        },
        data: data,
      };

      axios(config)
        .then(function (response) {
          localStorage.setItem("id", JSON.stringify(response.data.id));
          window.location.href = response.data.url;
        })
        .catch(function (error) {
          console.log(error);
        });
    },

    //paystack initialization
    pancake() {
      var axios = require("axios");
      var data = JSON.stringify({
        amount: this.pancakeAmount,
        email: this.pancakeEmail,
      });

      var config = {
        method: "post",
        url: "https://api.paystack.co/transaction/initialize",
        headers: {
          Authorization:
            "Bearer sk_test_0eb87185b90ad5bc1b42ef632afdb67837333bfa",
          "Content-Type": "application/json",
          Cookie:
            "sails.sid=s%3ARnICnxUM-pHyFa3gFZ0VmNaJ0wJA-5Kw.hVhEbfB%2BqxuCUVaUj0eyHuZCmyt3tk85oXgNMBX27Q8",
        },
        data: data,
      };
      axios(config)
        .then(function (response) {
          localStorage.setItem(
            "reference",
            JSON.stringify(response.data.data.reference)
          );
          window.location.href = response.data.data.authorization_url;
        })
        .catch(function (error) {
          console.log(error);
        });
    },

    pizza() {
      var axios = require("axios");
      var data = JSON.stringify({
        amount: this.amount,
        email: this.email,
      });

      var config = {
        method: "post",
        url: "https://api.paystack.co/transaction/initialize",
        headers: {
          Authorization:
            "Bearer sk_test_0eb87185b90ad5bc1b42ef632afdb67837333bfa",
          "Content-Type": "application/json",
          Cookie:
            "sails.sid=s%3ARnICnxUM-pHyFa3gFZ0VmNaJ0wJA-5Kw.hVhEbfB%2BqxuCUVaUj0eyHuZCmyt3tk85oXgNMBX27Q8",
        },
        data: data,
      };
      console.log("email", this.email);
      console.log("amount", this.amount)
      axios(config)
        .then(function (response) {
          localStorage.setItem(
            "reference",
            JSON.stringify(response.data.data.reference)
          );
          window.location.href = response.data.data.authorization_url;
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