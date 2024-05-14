<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/pengunjung/tambah">
                    <div class="card bg-pengunjung rounded-5">
                        <div class="card-body">
                            <h2 class="">pengunjung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/buku">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>cari buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <h2 class="mt-5" style="font-style: margin-left 100px;">STATISTIC</h2>
            <div class="col-lg-6">
                <div class="card statistic rounded-5">
                    <div class="card-body">
                        <h1>3</h1>
                        <h2>pengunjung</h2>
                    </div>
                </div>
            </div>
            <div class="col-lg-6">
                <div class="card bg-statistic rounded-5">
                    <div class="card-body">
                        <h1>200</h1>
                        <h2>BUKU</h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #030303;
}

.card.bg-pengunjung {
    background-image: url('~/assets/img/bg-home-kunjungan.jpeg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
    -webkit-text-fill-color: #030303;
}

.card.bg-buku {
    background: url('~/assets/img/bg-home-cari-buku.jpg');
    background-size: cover;
    -webkit-text-fill-color: #030303;
}

.card.statistic {
    background-repeat: no-repeat;
    background-position: center center;
    background-color: #F6AAF8;
}

.card.bg-statistic {
    background-color: #51A6F5;
    background-repeat: no-repeat;
}
</style>