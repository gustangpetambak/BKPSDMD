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
            <span>Semua Pengajuan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="3">
          <nuxt-link to="/admin/activities">
            <a-icon type="book" />
            <span>Daftar Kegiatan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="4">
          <nuxt-link to="/admin/kantor">
            <a-icon type="cluster" />
            <span>Daftar Kantor</span>
          </nuxt-link>
        </a-menu-item>
        <a-sub-menu key="sub2">
          <span slot="title">
            <a-icon type="appstore" />
            <span>Manajemen</span>
          </span>
          <a-menu-item key="9">
            <nuxt-link to="/admin/manajemen/diklat">Diklat / Kegiatan</nuxt-link>
          </a-menu-item>
          <a-menu-item key="10">
            <nuxt-link to="/admin/manajemen/room">Tempat Kegiatan</nuxt-link>
          </a-menu-item>
        </a-sub-menu>
        <a-menu-item key="5">
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

      <!-- menu MEMBER -->

      <a-menu-item-group key="g3">
        <template slot="title">
          <span class="text-uppercase">Menu Member</span>
        </template>
        <a-menu-item key="g3-1">
          <nuxt-link to="/member/activities">
            <a-icon type="book" />
            <span>Daftar Kegiatan</span>
          </nuxt-link>
        </a-menu-item>
        <a-menu-item key="g3-1">
          <nuxt-link to="/member/profile">
            <a-icon type="user" />
            <span>Pengaturan Profil</span>
          </nuxt-link>
        </a-menu-item>
      </a-menu-item-group>
    </a-menu>
  </div>
</template>