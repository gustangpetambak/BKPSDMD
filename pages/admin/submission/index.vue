<template>
  <div class="container">
    <div class="title">Daftar Pengajuan</div>

    <a-table :columns="columns" :dataSource="data" :scroll="{ x: 980 }">
      <span slot="action" slot-scope="text, record">
        <a @click="showApprove" class="color-green">Approve</a>
        <a-divider type="vertical" />
        <a @click="showReject" class="color-red">Tolak</a>
      </span>
    </a-table>

    <!-- if approve show modal -->
    <a-modal
      title="Konfirmasi Persetujuan Pengajuan"
      :footer="false"
      v-model="visibleApprove"
      @ok="handleApprove"
    >
      <a-form layout="vertical" :form="form" @submit="handleSubmitApprove" hideRequiredMark>
        <a-form-item label="Tempat Kegiatan">
          <a-select
            v-decorator="['tempat',{rules: [{ required: true, message: 'Harus di isi!' }]}]"
            placeholder="Pilih Tempat Kegiatan"
            showSearch
          >
            <a-select-option :value="1">Campus I</a-select-option>
            <a-select-option :value="2">Campus II</a-select-option>
          </a-select>
        </a-form-item>

        <a-form-item label="Ruangan Kegiatan">
          <a-select
            v-decorator="['room',{rules: [{ required: true, message: 'Harus di isi!' }]}]"
            placeholder="Pilih Ruangan Kegiatan"
            showSearch
          >
            <a-select-option :value="1">IB Lantai 2</a-select-option>
            <a-select-option :value="2">3A Lantai 1</a-select-option>
          </a-select>
        </a-form-item>

        <a-form-item label="Widiasuara/Pengajar">
          <a-select
            v-decorator="['pengajar',{rules: [{ required: true, message: 'Harus di isi!' }]}]"
            placeholder="Pilih Widiasuara/Pengajar"
            showSearch
          >
            <a-select-option :value="1">Widya Pitaloka</a-select-option>
            <a-select-option :value="2">Nur Elsa</a-select-option>
          </a-select>
        </a-form-item>

        <a-button type="primary" html-type="submit">Kirim</a-button>
      </a-form>
    </a-modal>

    <!-- if reject show modal -->
    <a-modal
      title="Konfirmasi Penolakan Pengajuan"
      :footer="false"
      v-model="visibleReject"
      @ok="handleReject"
    >
      <a-form layout="vertical" :form="form" @submit="handleSubmitReject" hideRequiredMark>
        <a-form-item label="Alasan Penolakan">
          <a-textarea
            :rows="4"
            v-decorator="['rejectDesc',{rules: [{ required: true, message: 'Harus di isi!' }]}]"
          />
        </a-form-item>

        <a-button type="primary" html-type="submit">Kirim</a-button>
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
      visibleApprove: false,
      data,
      columns
    };
  },
  methods: {
    showApprove() {
      this.visibleApprove = true;
    },
    handleApprove() {
      this.visibleApprove = false;
    },
    handleSubmitApprove(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.visibleApprove = false;
        }
      });
    },

    showReject() {
      this.visibleReject = true;
    },
    handleReject() {
      this.visibleReject = false;
    },
    handleSubmitReject(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.visibleReject = false;
        }
      });
    }
  }
};
</script>