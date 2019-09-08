<template>
  <div class="container">
    <a-row :gutter="16" type="flex" justify="space-around" align="middle">
      <a-col :xs="24" sm="12" :md="12">
        <div class="title">Daftar Pengajuan</div>
      </a-col>
      <a-col :xs="24" sm="12" :md="12" class="text-right">
        <a-button
          @click="showSubmission"
          type="primary"
          icon="plus"
          :style="{ marginRight: '16px' }"
        >Buat Pengajuan</a-button>
      </a-col>
    </a-row>
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

    <!-- if add submission show modal -->
    <a-modal
      title="Buat Pengajuan"
      :footer="false"
      v-model="visibleSubmission"
      @ok="handleSubmission"
    >
      <a-form layout="vertical" :form="form" @submit="handleSubmit" hideRequiredMark>
        <a-form-item label="Jenis Kegiatan" has-feedback>
          <a-select
            v-decorator="[
          'select',
          {rules: [{ required: true, message: 'Harus di isi!' }]}
        ]"
            placeholder="Pilih Jenis Kegiatan"
          >
            <a-select-option value="1">Kegiatan 1</a-select-option>
            <a-select-option value="2">Kegiatan 2</a-select-option>
          </a-select>
        </a-form-item>

        <a-form-item label="Tanggal Kegiatan" has-feedback>
          <a-date-picker style="width: 100%" v-decorator="['date-picker', config]" />
        </a-form-item>

        <a-form-item label="Jumlah Peserta" has-feedback>
          <a-input
            v-decorator="[
          'jumlahpeserta',
          {
            rules: [{ required: true, message: 'Harus di isi!' }]
          }
        ]"
          />
        </a-form-item>
        <a-button type="primary" html-type="submit">Kirim Pengajuan</a-button>
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
      visibleSubmission: false,
      data,
      columns,
      config: {
        rules: [{ type: "object", required: true, message: "Pilih Tanggal!" }]
      }
    };
  },
  methods: {
    showReject() {
      this.visibleReject = true;
    },
    handleReject() {
      this.visibleReject = false;
    },
    showSubmission() {
      this.visibleSubmission = true;
    },
    handleSubmission() {
      this.visibleSubmission = false;
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