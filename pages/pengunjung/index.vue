<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
               
                <div class="my-3">
                    <form @submit.prevent="getPengunjung">
                    <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Filter..">
                 </form>
                </div>
                <div>menampilkan {{ visitors.length }} pengunjung dari {{ visitor }} </div>
                <table class="table">
                    <thead>
                        <tr>
                            <td>#</td>
                            <td>nama</td>
                            <td>keanggotaan</td>
                            <td>waktu</td>
                            <td>keperluan</td>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(visitor,i) in visitors" :key="i">
                            <td>{{ i+1 }}</td>
                            <td>{{ visitor.nama }}</td>
                            <td>{{ visitor.keanggotaan.nama }}</td>
                            <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
                            <td>{{ visitor.keperluan.nama }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>
<script setup>
const supabase = useSuppabaseClient()

const visitors  = ref([])

const getPengunjung = async () => {
    const{data, error } = await supabase.from('pengunjung').select('*,keanggotaan(*), keperluan(*)')
    if(data) visitors.value = data
}

onMounted(() => {
    getPengunjung()
})
</script>