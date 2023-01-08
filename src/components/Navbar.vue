<template>
  <div
    class="w-screen bg-neutral-900 text-white md-h-24 h-16 grid grid-cols-6 gap-x-5 content-center px-5"
  >
    <div class="cols-1 w-8 h-auto">
      <img src="../assets/img/instagram-glyph-1.svg" class="" alt="" />
    </div>
    <div class="cols-4 col-span-4 self-center">
      <label class="relative text-gray-400 focus-within:text-gray-600 block">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="pointer-events-none w-8 h-8 absolute top-1/2 transform -translate-y-1/2 left-3"
          viewBox="0 5 80 40"
          fill="currentColor"
        >
          <path
            d="M 21 3 C 11.621094 3 4 10.621094 4 20 C 4 29.378906 11.621094 37 21 37 C 24.710938 37 28.140625 35.804688 30.9375 33.78125 L 44.09375 46.90625 L 46.90625 44.09375 L 33.90625 31.0625 C 36.460938 28.085938 38 24.222656 38 20 C 38 10.621094 30.378906 3 21 3 Z M 21 5 C 29.296875 5 36 11.703125 36 20 C 36 28.296875 29.296875 35 21 35 C 12.703125 35 6 28.296875 6 20 C 6 11.703125 12.703125 5 21 5 Z"
          ></path>
        </svg>

        <input
          type="text"
          class="bg-zinc-700 rounded-full w-full h-8 px-10 pb-1"
          placeholder="Buscar"
        />
      </label>
    </div>
    <div class="cols-1 self-center justify-self-center">
      <svg
        height="25px"
        width="25px"
        version="1.1"
        id="Capa_1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        viewBox="0 0 60.671 60.671"
        xml:space="preserve"
        fill="#000000"
      >
        <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
        <g id="SVGRepo_iconCarrier">
          <g>
            <g>
              <ellipse
                style="fill: #fff;"
                cx="30.336"
                cy="12.097"
                rx="11.997"
                ry="12.097"
              ></ellipse>
              <path
                style="fill: #fff;"
                d="M35.64,30.079H25.031c-7.021,0-12.714,5.739-12.714,12.821v17.771h36.037V42.9 C48.354,35.818,42.661,30.079,35.64,30.079z"
              ></path>
            </g>
          </g>
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>
