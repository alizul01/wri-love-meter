<template>
  <div class="flex justify-center items-center flex-col">
    <div class="flex flex-col items-start" id="nama1">
      <label for="nama1">Masukkan Nama Kamu</label>
      <input
        type="text"
        v-model="name"
        placeholder="Nama Kamu"
        class="
          w-96
          p-2
          rounded-lg
          border-2 border-gray-300
          focus:outline-none focus:border-blue-500
        "
      />
    </div>

    <div class="flex flex-col items-start mt-4" id="nama2">
      <label for="nama2">Masukkan Nama Doimu</label>
      <input
        type="text"
        v-model="partner"
        placeholder="Nama Pasanganmu"
        class="
          w-96
          p-2
          rounded-lg
          border-2 border-gray-300
          focus:outline-none focus:border-blue-500
        "
      />
    </div>

    <div class="flex flex-col items-start mt-4" id="chattingan">
      <label for="chattingan">Kamu sering chatting sama dia atau nggak?</label>
      <select
        v-model="chatting"
        class="
          w-96
          p-2
          rounded-lg
          border-2 border-gray-300
          focus:outline-none focus:border-blue-500
        "
      >
        <option value="1">Sering</option>
        <option value="2">Kadang-kadang</option>
        <option value="3">Jarang</option>
        <option value="4">Tidak pernah</option>
      </select>
    </div>

    <!-- Sering ketemu sama dia nggak nih? radio type -->
    <div class="flex flex-col items-start mt-4" id="ketemu">
      <label for="ketemu">Kalian sering ketemuan ngga?</label>
      <select
        v-model="ketemu"
        class="
          w-96
          p-2
          rounded-lg
          border-2 border-gray-300
          focus:outline-none focus:border-blue-500
        "
      >
        <option value="1">Sering</option>
        <option value="2">Kadang-kadang</option>
        <option value="3">Jarang</option>
        <option value="4">Tidak pernah</option>
      </select>
    </div>

    <button
      :disabled="!name || !partner || chatting == 0 || ketemu == 0"
      :class="{
        'bg-gray-500': !name || !partner || chatting == 0 || ketemu == 0,
        'bg-blue-500': name && partner,
      }"
      class="text-white font-bold py-2 px-4 rounded mt-4"
      @click="calculateLove()"
    >
      <span v-if="name && partner && chatting != 0 && ketemu != 0"
        >Hitung Love Meter</span
      >
      <span v-else>Lengkapin dulu boy!</span>
    </button>

    <!-- make box white for result -->
    <div
      class="mt-8 mx-24 bg-white w-[80vw] flex items-start flex-col shadow-md"
    >
      <h1 class="text-2xl font-bold p-4">Hasil</h1>

      <p class="p-4">
        {{ result }}
      </p>

      <div id="loveParam">
        <div class="flex flex-col items-start p-4">
          <h1 class="text-xl font-bold">Love Parameter</h1>
          <p class="mt-2 font-normal text-lg">
            <span v-if="loveParam >= 93"
              >Udahlah gas aja ini mah, gausah kelamaan pdkt!</span
            >
            <span v-else-if="loveParam >= 90"
              >Wah, kamu sama dia cocok banget lho! Gas pacaran aja sih
              wkwk</span
            >
            <span v-else-if="loveParam >= 80"
              >Hmm kalo nilainya segini, udah oke sie tapi lebih semangat lagi
              pdktnya!</span
            >
            <span v-else-if="loveParam >= 70"
              >Gimana ya bilangnya, sudah oke tapi saran gue mah sering chat dia
              lagi deh!</span
            >
            <span v-else-if="loveParam >= 60 && loveParam <= 70"
              >Poinmu rendah, cepet ungkapin perasaan daripada diambil orang
              lain lho!</span
            >
            <span v-else-if="loveParam >= 30 && loveParam <= 59"
              >Aduh nilainya rendah banget, cepetin deh pdktnya!</span
            >

            <span v-else-if="loveParam >= 0 && loveParam <= 29"
              >Aduh ini mah ngebadut namanya 😭</span
            >

            <span v-else> Belum ada nilai </span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core"; // @ is an alias to /src
export default defineComponent({
  name: "HomeView",
  data() {
    return {
      name: "",
      partner: "",
      result: "",
      loveParam: -1,
      chatting: 0,
      ketemu: 0,
    };
  },
  methods: {
    calculateLove() {
      const name: string = this.name;
      const partner: string = this.partner;
      let mathRandom = Math.round(Math.random() * 100);

      if (mathRandom > 90) {
        mathRandom = 75;
      }

      const love =
        name.length + partner.length + this.chatting * this.ketemu + mathRandom;

      if (love > 100) {
        this.loveParam = 100;
      } else {
        this.loveParam = love;
      }
      if (name && partner) {
        this.result = `${name} dan ${partner} memiliki persentase ${this.loveParam}% untuk saling mencintai`;
      } else {
        this.result = "Mohon isi semua form";
      }

      if (!name || !partner || this.chatting == 0 || this.ketemu == 0) {
        this.result = "Mohon isi semua form";
        this.loveParam = -1;
      }
    },
  },
});
</script>
