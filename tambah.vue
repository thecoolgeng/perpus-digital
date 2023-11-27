<template>
<div class="row">
  <div class="col">   
    <h2 class="text-center">isi pengunjung</h2>
    <div v-if="sukses" class="alert alert-succes">berhasil tersimpan</div>
    <form @submit.prevent="$event=>simpan()">
      <div class="mb-3">
        <input v-model="form.nama" type="text" class="form-control" placeholder="isi nama">
      </div>
      <div class="mb-3">
        <select v-model="form.anggota" class="form-control">
        <option value="">pilih keanggotaan</option>
        <option value="1">SISWA</option>
        <option value="2">GURU</option>
        <option value="3">STAF</option>
      </select>
      </div>
      <div v-if="form.anggota == '1'" class="mb-3">
        <input v-model="form.kelas" type="text" class="form-control" placeholder="kelas">
      </div>
      <div class="mb-4">
        <textarea v-model="form.keperluan" cols="30" rows="10" placeholder="keperluan" class="form-control"></textarea>
      </div>
      <button type="submit" class="btn btn-outline-primary">kirim</button>
      <NuxtLink to="/">kembali</NuxtLink>
    </form></div>
</div>
</template>

<script setup>
const supabase=useSupabaseClient()
const form=reactive({
  nama:"",
  anggota:"",
  kelas:"",
  keperluan:"",
});
const sukses = ref(false);

async function simpan(){
  sukses.value=false;
  const {error}= await supabase
  .from('pengunjung')
  .insert(form);
  if (!error){
    sukses.value=true
    form.nama=""
    form.anggota=""
    form.kelas=""
    form.keperluan=""
  }
}
</script>