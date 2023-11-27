<template>
      <h2><center>Riwayat kunjungan</center></h2>
      <NuxtLink to="/tambah">isi kunjungan</NuxtLink>
  <div>
    <table class="table">
  <thead class="table-primary">
    <tr>
          <th>#</th>
          <th>tanggal dan waktu</th>
          <th>nama</th>
          <th>anggota</th>
          <th>keperluan</th>
          <th>kelas</th>
        </tr>
  </thead>
  <tbody>
    <tr v-for="pengunjung in visitors" :key="pengunjung.id">
          <td>{{pengunjung.id}}</td>
          <td>{{ pengunjung.tanggal}}{{ pengunjung.waktu}}</td>
          <td>{{pengunjung.nama}}</td>
          <td>{{pengunjung.anggota.keanggotaan}}</td>
          <td>{{pengunjung.keperluan}}</td>
          <td>{{pengunjung.kelas}}</td>
          <td>
            <span v-if="pengunjung.kelas"></span>
            <span v-else>-</span>
          </td>
        </tr> 
  </tbody>
</table>
  </div>
</template>
<script setup>
const client=useSupabaseClient()
const visitors=ref([])

async  function getData(){
  const{data,error}= await client
  .from("pengunjung")
  .select("id,tanggal,waktu,nama,anggota(keanggotaan),kelas,keperluan");
  if (data)visitors.value = data
}
onMounted(() => getData())
</script>