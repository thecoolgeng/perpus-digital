<template>
  <div>
    <h1><center>isi pengunjung</center></h1>
    <form>
      <input v-model="form.nama" type="text" placeholder="nama " required> <br>
      <select v-model="form.anggota">
        <option value="">pilih keanggotaan</option>
        <option v-for="a in anggota" :key="a.id" :value="a.id">{{ a.nama }}</option>
      </select><br>
      <textarea v-model="form.keperluan" cols="30" rows="10" placeholder="keperluan"></textarea><br>
      <button type="submit">kirim</button>
      <NuxtLink to="/">kembali</NuxtLink>
    </form>
  </div>
</template>
<script setup>
const supabase=useSupabaseClient()
const anggota=ref([])
const form=reactive({
  nama:"",
  anggota:"",
  keperluan:""
})

async function getanggota(){
  const{data,error}= await supabase.from('anggota').select()
  if (data) anggota.value=data
}
async function simpankunjungan(){
  const {error}= await supabase.from('pengunjung').insert(from)
}
onMounted(() => getanggota())
</script>