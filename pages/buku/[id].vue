<template>
    <h2 class="text-start my-4">{{ buku.judul }}</h2>
    <div class="row">
        <div class="col-md-3">
            <img :src="buku.cover" class="cover" alt="cover buku">
        </div>
        <div class="col-md-6">
            <div class="badge bg-primary p-2">{{ buku.kategori }}</div>
            <ul class="list-group list-group-flush">
                <li class="list-group-item">Penulis: {{ buku.penulis }}</li>
                <li class="list-group-item">Penerbit: {{ buku.penerbit }}</li>
                <li class="list-group-item">Tahun Terbit: {{ buku.tahun_terbit }}</li>
                <li class="list-group-item">{{ buku.deskripsi }}</li>
            </ul>
        </div>
    </div>
    <nuxt-link to="../"
                ><button
                  type="submit"
                  class="btn btn-lg rounded-5 px-5 bg-light"
                  style="float: right"
                >
                  KEMBALI
                </button></nuxt-link>
    </template>

<style scoped>
  .card-body {
    width: 100%;
    height: 250%;
    padding: 0;
  }
  .cover {
    width: 100%;
    height: 100%;

  }
  </style>

<script setup>
import { onMounted } from 'vue';

const supabase = useSupabaseClient()

const route = useRoute()
const buku = ref([])

const getBookById = async () =>  {
    const {data, error} = await supabase.from('buku').select(`*,kategori(*)`)
    .eq('id', route.params.id)
    if(data)buku.value=data[0]
}

onMounted(() => {
getBooks()
})
</script>