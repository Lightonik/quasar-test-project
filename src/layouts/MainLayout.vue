<template>
  <q-layout view="lHh Lpr lFf">
    <q-header
      class="bg-white text-blue-grey-10"
      bordered
    >
      <q-toolbar class="constrain">
        <q-btn 
          to="/camera"
          class="large-screen-only"
          flat round icon="eva-camera-outline" 
          size="18px" dense 
          />
        <q-separator 
          vertical 
          spaced 
          class="large-screen-only"
          />
        <q-toolbar-title
          class="text-grand-hotel text-bold"  
        >
          Quasar App
        </q-toolbar-title>
        <q-btn 
          to="/"
          class="large-screen-only"
          flat round icon="eva-home-outline" size="18px" dense />

      </q-toolbar>
    </q-header>

    <q-footer 
      class="bg-white small-screen-only"
      bordered
    >
        <q-tabs 
          class="text-blue-grey-10"
          active-color="primary"
          indicator-color="transparent"
        >
          <q-route-tab 
          to="/"
          icon="eva-home-outline" label="Home" />
          <q-route-tab
          to="/camera"
          icon="eva-camera-outline" label="Camera" />
        </q-tabs>
      </q-footer>

       
    <q-page-container class="bg-grey-2">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  
  data () {
    return {
    }
  }
}
</script>

<style lang="sass">
  .q-toolbar
    @media (min-width: $breakpoint-sm-min)  
      height: 64px
  .q-toolbar__title
    font-size: 32px
    @media (max-width: $breakpoint-xs-max)
      text-align: center
  .q-footer
    .q-tab__icon
      font-size: 32px
</style>