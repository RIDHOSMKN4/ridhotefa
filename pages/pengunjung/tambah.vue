<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h1 class="text-center my-4">isi buku kunjungan</h1>
                <form @submit.prevent="kirimData">
                    <div class="mb-3">
                        <input v-model="form.nama" type="text" class="form-control form-control-lg form-select rounded-5"
                            placeholder="nama...." aria-describedby="basic-addon1">
                    </div>
                    <div class="mb-3">
                        <select input v-model="form.keanggotaan" class="form-control form-control-lg form-select rounded-5">
                            <option value="">keanggotaan.......</option>
                            <option v-for="(member, i) in members" :key="i" :value="member.id">{{ member.nama }}</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <div class="row">
                            <div class="col-md-4">
                                <select v-model="form.tingkat" class="form-cotrol form-control-lg form-select rounded-5 mb-2">
                                    <option value="">tingkat</option>
                                    <option value="x">x</option>
                                    <option value="xi">xi</option>
                                    <option value="xii">xii</option>
                                </select>
                            </div>
                            <div class="col-md-4">
                                <select v-model="form.jurusan" class="form-cotrol form-control-lg form-select rounded-5 mb-2">
                                    <option value="">jurusan</option>
                                    <option value="pplg">pplg</option>
                                    <option value="tkj">tkj</option>
                                    <option value="tsm">tsm</option>
                                    <option value="dkv">dkv</option>
                                    <option value="toi">toi</option>
                                </select>
                            </div>
                            <div class="col-md-4">
                                <select v-model="form.kelas" class="form-cotrol form-control-lg form-select rounded-5 mb-2">
                                    <option value="">kelas</option>
                                    <option value="1">1</option>
                                    <option value="2">2</option>
                                    <option value="3">3</option>
                                    <option value="4">4</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    <div class="mb-3">
                        <select v-model="form.keperluan" class="form-cotrol form-control-lg form-select rounded-5 ">
                            <option value="">keperluan</option>
                            <option v-for="(item, i) in objectives" :key="i" :value="item.id">{{item.nama }}</option>
                        </select>
                    </div>
                    <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">KIRIM</button>
                </form>
            </div>
        </div>
    </div>
</template>
<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])

const form = ref({
    nama: "",
    keanggotaan: "",
    tingkat: "",
    jurusan: "",
    kelas: "",
    keperluan: "",
})

const kirimData = async() => {
    const{  error } = await supabase.from('pengunnjung').insert([form.value])
    if(!error ) navigateTo('/pengunjung')
}

const getKeanggotaan = async () =>{
    const { data, error } = await supabase.from('keanggotaan').select('*')

    if(data) members.value = data
}

const getKeperluan = async() => {
    const { data, error } = await supabase.from('keperluan').select('*')
    if(data) objectives.value=data
}

onMounted(() =>{
    getKeanggotaan()
    getKeperluan()
})
</script>