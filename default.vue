<template>
    <div class="container">
      <div class="row bg-primary text-light align-items-start">
        <div class="col-lg-1">
          <img src="~/assets/img/logo.png"
          alt=""
          width="80"
          height="80"
          class="d-inline-block align-text-top left-20">
        </div>
        <div class="col-lg">
          <h1>BUKU PENGUNJUNG PERPUSTAKAAN</h1>
          <P>
            JL.DEPOK,SUKAMENAK,KEC.PURBARATU,KAB.TASIKMALAY,JAWA BARAT
          </P>
        </div>
        <div class="col">
          <img src="~/assets/img/logokelompok2.png"
          alt=""
          width="150"
          height="150"
          class="d-inline-block align-text-top right-20">
        </div>
      </div>
      <slot />
  </div>
</template>