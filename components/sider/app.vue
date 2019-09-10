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
      <a-menu-item-group key="g1">
        <template slot="title">
          <span class="text-uppercase">Menu Admin</span>
        </template>
        <a-menu-item key="2">
          <nuxt-link to="/admin/submission">
            <a-icon type="tags" />
            <span>Daftar Pengajuan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="3">
          <nuxt-link to="/admin/activities">
            <a-icon type="book" />
            <span>Daftar Kegiatan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="4">
          <nuxt-link to="/admin/report">
            <a-icon type="printer" />
            <span>Laporan</span>
          </nuxt-link>
        </a-menu-item>
      </a-menu-item-group>

      <!-- menu BKD kab/kota -->

      <a-menu-item-group key="g2">
        <template slot="title">
          <span class="text-uppercase">Menu BKD</span>
        </template>
        <a-menu-item key="g2-1">
          <nuxt-link to="/bkd/submission">
            <a-icon type="tags" />
            <span>Pengajuan Kegiatan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="g2-2">
          <nuxt-link to="/bkd/activities">
            <a-icon type="book" />
            <span>Daftar Kegiatan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="g2-3">
          <nuxt-link to="/bkd/skpd">
            <a-icon type="bars" />
            <span>Daftar SKPD</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="g2-4">
          <nuxt-link to="/bkd/report">
            <a-icon type="printer" />
            <span>Laporan</span>
          </nuxt-link>
        </a-menu-item>
      </a-menu-item-group>

      <!-- <a-menu-item key="3">
        <nuxt-link to="/admin/rundown">
          <a-icon type="schedule" />
          <span>Rundown</span>
        </nuxt-link>
      </a-menu-item>-->
      <!-- <a-menu-item key="5">
        <a-icon type="idcard" />
        <span>Profil Saya</span>
      </a-menu-item>-->
    </a-menu>
  </div>
</template>