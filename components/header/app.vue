<template>
  <div>
    <div class="d-flex align-items-center">
      <div class="hidden-dekstop" style="margin-right:8px">
        <a @click="showDrawer">
          <a-avatar style="backgroundColor:#fafafa;color:#484848" icon="menu-fold" />
        </a>
      </div>
      <div style="margin-right: 16px" class="hidden-dekstop fs-18 cr-black">BKPSDMD</div>
      <div class="hidden-mobile"><a-badge status="success" text="Online" /></div>

      <div class="ml-auto">
        <a-avatar class="hidden-mobile" icon="poweroff" style="margin-right: 8px" />
        <a-avatar class="hidden-dekstop" style="backgroundColor:#fafafa" size="large" src="/user.png" />
      </div>
    </div>

    <a-drawer placement="left" :closable="false" @close="onClose" :visible="visible">
      <div slot="title">
        <div class="d-flex align-items-center">
          <div>BKPSDMD</div>
          <div class="ml-auto">
            <a-button @click="onClose" shape="circle" icon="close" />
          </div>
        </div>
      </div>

      <div class="avatar d-flex align-items-center" style="margin-bottom: 16px">
        <div class="avatar-item" style="margin-right: 8px">
          <a-avatar size="large" src="/user.png" />
        </div>
        <div class="name-user fs-14 cr-black">Jordi Alba Mustafa</div>
      </div>

      <a-menu @click="handleClick" :defaultSelectedKeys="['1']" mode="inline">
        <a-menu-item key="1">
          <nuxt-link to="/dashboard">
            <a-icon type="dashboard" />
            <span>Dashboard</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="2">
          <nuxt-link to="/admin/submission">
            <a-icon type="tags" />
            <span>Daftar Pengajuan</span>
          </nuxt-link>
        </a-menu-item>
        <!-- <a-menu-item key="3">
          <nuxt-link to="/admin/rundown">
            <a-icon type="schedule" />
            <span>Rundown</span>
          </nuxt-link>
        </a-menu-item> -->
        <a-menu-item key="4">
          <nuxt-link to="/admin/report">
            <a-icon type="printer" />
            <span>Laporan</span>
          </nuxt-link>
        </a-menu-item>
        <!-- <a-menu-item key="5">
        <a-icon type="idcard" />
        <span>Profil Saya</span>
        </a-menu-item>-->
      </a-menu>
    </a-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false
    };
  },
  methods: {
    showDrawer() {
      this.visible = true;
    },
    onClose() {
      this.visible = false;
    },
    handleClick() {
      this.visible = false;
    }
  }
};
</script>