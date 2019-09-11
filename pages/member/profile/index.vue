<template>
  <div>
    <div class="container">
      <a-row :gutter="16" type="flex" justify="space-around" align="middle">
        <a-col :xs="24" :sm="12" :md="12">
          <div class="title fs-18">Profil Saya</div>
        </a-col>
        <a-col :xs="24" :sm="12" :md="12" class="text-right">
          <a-button
            @click="showEdit"
            type="danger"
            icon="edit"
            :style="{ marginRight: '16px' }"
          >Edit</a-button>
        </a-col>
      </a-row>

      <a-list itemLayout="horizontal" style="padding: 0 20px 10px 20px">
        <a-list-item>
          <a-row :gutter="8" style="width: 100%">
            <a-col :xs="24" :sm="6" :md="4">
              <span class="fs-14 cr-gray">SKPD</span>
            </a-col>
            <a-col :xs="24" :sm="18" :md="20">
              <span class="fs-14 cr-black">Badan Pemberdayaan Masyarakat</span>
            </a-col>
          </a-row>
        </a-list-item>
        <a-list-item>
          <a-row :gutter="8" style="width: 100%">
            <a-col :xs="24" :sm="6" :md="4">
              <span class="fs-14 cr-gray">NIP</span>
            </a-col>
            <a-col :xs="24" :sm="18" :md="20">
              <span class="fs-14 cr-black">09298227727277277</span>
            </a-col>
          </a-row>
        </a-list-item>
        <a-list-item>
          <a-row :gutter="8" style="width: 100%">
            <a-col :xs="24" :sm="6" :md="4">
              <span class="fs-14 cr-gray">Nama Lengkap</span>
            </a-col>
            <a-col :xs="24" :sm="18" :md="20">
              <span class="fs-14 cr-black">Jordi Alba S.kom</span>
            </a-col>
          </a-row>
        </a-list-item>
        <a-list-item>
          <a-row :gutter="8" style="width: 100%">
            <a-col :xs="24" :sm="6" :md="4">
              <span class="fs-14 cr-gray">No. Telepon</span>
            </a-col>
            <a-col :xs="24" :sm="18" :md="20">
              <span class="fs-14 cr-black">085213247455</span>
            </a-col>
          </a-row>
        </a-list-item>
        <a-list-item>
          <a-row :gutter="8" style="width: 100%">
            <a-col :xs="24" :sm="6" :md="4">
              <span class="fs-14 cr-gray">Alamat</span>
            </a-col>
            <a-col :xs="24" :sm="18" :md="20">
              <span class="fs-14 cr-black">Jl. BTP Blok A No 537</span>
            </a-col>
          </a-row>
        </a-list-item>
      </a-list>

      <!-- if edit profile show modal -->
      <a-modal title="Edit" :footer="false" v-model="visibleEdit" @ok="handleEdit" centered>
        <a-form layout="vertical" :form="form" @submit="handleSubmitEdit" hideRequiredMark>
          <a-form-item label="Nama SKPD" has-feedback>
            <a-select
              v-decorator="[
          'skpd',
          {rules: [{ required: true, message: 'Harus di isi!' }]}
        ]"
              placeholder="Pilih SKPD"
              showSearch
            >
              <a-select-option :value="1">Badan Pemberdayaan Masyarakat</a-select-option>
            </a-select>
          </a-form-item>

          <a-form-item label="Nama Lengkap" has-feedback>
            <a-input
              v-decorator="['nameEdit',{initialValue: ['Jordi Alba S.kom'], rules: [{ required: true, message: 'Harus di isi!' }]}]"
            />
          </a-form-item>

          <a-form-item label="NIP" has-feedback>
            <a-input
              v-decorator="['nipEdit',{initialValue: ['09298227727277277'], rules: [{ required: true, message: 'Harus di isi!' }]}]"
            />
          </a-form-item>

          <a-form-item label="No. Telepon" has-feedback>
            <a-input
              v-decorator="['telpEdit',{initialValue: ['315049'], rules: [{ required: true, message: 'Harus di isi!' }]}]"
            />
          </a-form-item>

          <a-form-item label="Alamat">
            <a-textarea
              :rows="4"
              v-decorator="['addressEdit',{initialValue: ['Jl. Ahmad Yani No.2'], rules: [{ required: true, message: 'Harus di isi!' }]}]"
            />
          </a-form-item>
          <a-button type="primary" html-type="submit">Simpan Perubahan</a-button>
        </a-form>
      </a-modal>
    </div>
  </div>
</template>
<script>
export default {
  name: "profile",
  beforeCreate() {
    this.form = this.$form.createForm(this);
  },
  head() {
    return {
      title: "Pengaturan Profil"
    };
  },
  data() {
    return {
      visibleEdit: false
    };
  },
  methods: {
    showEdit() {
      this.visibleEdit = true;
    },
    handleEdit() {
      this.visibleEdit = false;
    },
    handleSubmitEdit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.visibleEdit = false;
        }
      });
    }
  }
};
</script>