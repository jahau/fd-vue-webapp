<template>
  <v-ons-page>
    <div class="profile-pic">
      <img src="../../../assets/freedomotic-logo.png">
    </div>

    <v-ons-list>
      <v-ons-list-item v-for="(item, index) in access" :key="item.title"
        @click="loadView(index)"
      >
        <div class="left">
          <v-ons-icon fixed-width class="list-item__icon" :icon="item.icon"></v-ons-icon>
        </div>
        <div class="center">
          {{ $t(item.title) }}
        </div>
      </v-ons-list-item>
    </v-ons-list>

    <v-ons-list-title style="margin-top: 10px">{{$t('online_resources')}}</v-ons-list-title>
    <v-ons-list>
      <v-ons-list-item v-for="item in links" :key="item.title"
        @click="loadLink(item.url)"
      >
        <div class="left">
          <v-ons-icon fixed-width class="list-item__icon" :icon="item.icon"></v-ons-icon>
        </div>
        <div class="center">
          {{ $t(item.title) }}
        </div>
        <div class="right">
          <v-ons-icon icon="fa-external-link"></v-ons-icon>
        </div>
      </v-ons-list-item>
    </v-ons-list>
  </v-ons-page>
</template>

<script>
export default {
  props: ['toggleMenu', 'setIndex'],

  methods: {
    loadView (index) {
      this.setIndex(index)
      this.toggleMenu()
    },
    loadLink (url) {
      window.open(url, '_blank')
    }
  },
  data () {
    return {
      links: [
        {
          title: 'official_site',
          icon: 'ion-navigate',
          url: 'https://www.freedomotic-iot.com'
        },
        {
          title: 'docs',
          icon: 'ion-document-text',
          url: 'https://http://freedomotic-user-manual.readthedocs.io'
        },
        {
          title: 'source_code',
          icon: 'ion-social-github',
          url: 'https://github.com/freedomotic/fd-vue-webapp'
        },
        {
          title: 'community',
          icon: 'ion-chatboxes',
          url: 'https://groups.google.com/forum/#!forum/freedom-domotics'
        },
        {
          title: 'report_bug',
          icon: 'ion-bug',
          url: 'https://goo.gl/forms/CqZZfBCHNx'
        }
      ],
      access: [
        {
          title: 'home',
          icon: 'ion-home, material:md-home'
        },
        {
          title: 'settings',
          icon: 'ion-gear-b, material:md-settings'
        },
        {
          title: 'plugins',
          icon: 'ion-cube, material:md-dashboard'
        },
        {
          title: 'logout',
          icon: 'ion-log-out, material:md-exit_to_app'
        }
      ]
    }
  }
}
</script>

<style scoped>
.profile-pic {
  width: 200px;
  margin: 20px auto 10px;
}

.profile-pic > img {
  display: block;
  max-width: 100%;
}

ons-list-item {
  color: #444;
}
</style>
