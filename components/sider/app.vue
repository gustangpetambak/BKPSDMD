<template>
  <div>
    <div class="brand-sider d-flex align-items-center">
      <!-- <div class="logo" :style="{ backgroundImage: 'url(/logo.png)' }" /> -->
      <div class="logo-text">BKPSDMD</div>
    </div>
    <div class="avatar d-flex align-items-center">
      <div class="avatar-item">
        <a-avatar :size="64" src="/user.png" />
        <div class="name-user">Jordi Alba Mustafa</div>
      </div>
    </div>
    <a-menu theme="dark" :defaultSelectedKeys="['1']" mode="inline">
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
      <a-menu-item key="3">
        <nuxt-link to="/admin/rundown">
          <a-icon type="schedule" />
          <span>Rundown</span>
        </nuxt-link>
      </a-menu-item>
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
  </div>
</template>