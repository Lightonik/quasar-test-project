<template>
  <q-page class="constrain q-pa-md">
    <div class="camera-frame q-pa-md">
      <img
        class="full-width"
        src="https://sun9-32.userapi.com/impf/c830608/v830608531/15cbb8/H2RclojnmtQ.jpg?size=2560x1920&quality=96&sign=cf30bf10bfdb2e90399e0685d48a3ac8&type=album">
    </div>
    <div class="text-center q-pa-md">
      <q-btn
        round
        color="grey-10"
        icon="eva-camera" 
        size="lg"
      />
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageCamera'
}
</script>

<style lang="sass">
  .camera-frame
    border: 2px solid $grey-10
    border-radius: 10px
</style>