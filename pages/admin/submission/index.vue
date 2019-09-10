<template>
  <div class="container">
    <div class="title">Daftar Pengajuan</div>

    <a-table :columns="columns" :dataSource="data" :scroll="{ x: 980 }">
      <span slot="action" slot-scope="text, record">
        <a href="javascript:;" class="color-green">Approve</a>
        <a-divider type="vertical" />
        <a @click="showReject" class="color-red">Tolak</a>
      </span>
    </a-table>

    <!-- if reject show modal -->
    <a-modal
      title="Apakah anda ingin menolak pengajuan ini ?"
      :footer="false"
      v-model="visibleReject"
      @ok="handleReject"
    >
      <a-form layout="vertical" hideRequiredMark>
        <a-form-item label="Alasan Penolakan">
          <a-textarea :rows="4" />
        </a-form-item>

        <a-button type="primary" @click="handleReject">Kirim</a-button>
      </a-form>
    </a-modal>
  </div>
</template>
<script>
const columns = [
  {
    title: "Nama Kegiatan",
    dataIndex: "name",
    key: "name"
  },
  { title: "SKPD", dataIndex: "skpd", key: "skpd" },
  { title: "Jumlah Peserta", dataIndex: "jumlah", key: "jumlah" },
  { title: "Waktu Kegiatan", dataIndex: "createdAt", key: "createdAt" },
  {
    title: "Action",
    key: "operation",
    fixed: "right",
    width: 150,
    scopedSlots: { customRender: "action" }
  }
];

const data = [
  {
    key: "1",
    name: "Diklat Prajabatan Golongan I Angkatan X dan XI Tahun 2019",
    skpd: "Dinas Perhubungan",
    createdAt: "Senin, 10 November 2019",
    jumlah: "40"
  },
  {
    key: "2",
    name: "Diklat Prajabatan Golongan II Angkatan X dan XI Tahun 2019",
    skpd: "Dinas Pengelolaan Kebersihan",
    createdAt: "Minggu, 17 November 2019",
    jumlah: "45"
  }
];

export default {
  name: "submission",
  beforeCreate() {
    this.form = this.$form.createForm(this);
  },
  head() {
    return {
      title: "Daftar Pengajuan Kegiatan - BKPSDMD"
    };
  },
  data() {
    return {
      visibleReject: false,
      data,
      columns
    };
  },
  methods: {
    showReject() {
      this.visibleReject = true;
    },
    handleReject() {
      this.visibleReject = false;
    },
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.visibleSubmission = false;
        }
      });
    }
  }
};
</script>