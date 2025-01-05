<template>
  <q-page class="constrain q-pa-md">

    <div class="row q-col-gutter-lg">
      <div class="col-12 col-sm-8">
      <q-card
        v-for="post in posts"
        :key="post.id"
        class="card-post q-mb-md"
        flat
        bordered>
          <q-item>
            <q-item-section avatar>
              <q-avatar>
                <img
                src="https://sun9-34.userapi.com/s/v1/ig2/62M90y9EKA4ApA-rL_sF8fLGus7PSUwLfj883qMy0U5hKg7Eofdoo5tfV1ZrXw5dMmJtK2IckeK3M6vaJDGueZc-.jpg?quality=96&crop=443,340,498,498&as=32x32,48x48,72x72,108x108,160x160,240x240,360x360,480x480&ava=1&u=MqjMmu8dAnN1bDFdyy_ukLvZ0FKgL68tmqW57MJQ7Ks&cs=200x200">
                </q-avatar>           
            </q-item-section>
            <q-item-section>
              <q-item-label class="text-bold">vit</q-item-label>
              <q-item-label caption> {{ post.location}} </q-item-label>
            </q-item-section>
          </q-item>
        <q-separator
        />
        <q-img
        :src="post.imageUrl"
        />
        <q-card-section>
        <div> {{ post.caption }} </div>
        <div class="text-caption"> {{ post.date | niceDate}} </div>
        </q-card-section>
        </q-card>
      </div>
      <div class="col-4 large-screen-only">
        <q-item class="fixed">
            <q-item-section avatar>
              <q-avatar size="48px">
                <img
                src="https://sun9-34.userapi.com/s/v1/ig2/62M90y9EKA4ApA-rL_sF8fLGus7PSUwLfj883qMy0U5hKg7Eofdoo5tfV1ZrXw5dMmJtK2IckeK3M6vaJDGueZc-.jpg?quality=96&crop=443,340,498,498&as=32x32,48x48,72x72,108x108,160x160,240x240,360x360,480x480&ava=1&u=MqjMmu8dAnN1bDFdyy_ukLvZ0FKgL68tmqW57MJQ7Ks&cs=200x200">
                </q-avatar>           
            </q-item-section>
            <q-item-section>
              <q-item-label class="text-bold">vit</q-item-label>
              <q-item-label caption> vit </q-item-label>
            </q-item-section>
          </q-item>
      </div>
    </div>


    
  </q-page>
</template>

<script>
import { date } from 'quasar'

export default {
  name: 'PageHome',
  data() {
    return {
      posts: [
        {
          id: 1,
          caption: 'Text',
          date: 1735911978535,
          location: 'Somewhere',
          imageUrl: 'https://sun9-32.userapi.com/impf/c830608/v830608531/15cbb8/H2RclojnmtQ.jpg?size=2560x1920&quality=96&sign=cf30bf10bfdb2e90399e0685d48a3ac8&type=album'
        },
        {
          id: 2,
          caption: 'Text',
          date: 1735911978535,
          location: 'Somewhere',
          imageUrl: 'https://sun9-32.userapi.com/impf/c830608/v830608531/15cbb8/H2RclojnmtQ.jpg?size=2560x1920&quality=96&sign=cf30bf10bfdb2e90399e0685d48a3ac8&type=album'
        },
        {
          id: 3,
          caption: 'Text',
          date: 1735911978535,
          location: 'Somewhere',
          imageUrl: 'https://sun9-32.userapi.com/impf/c830608/v830608531/15cbb8/H2RclojnmtQ.jpg?size=2560x1920&quality=96&sign=cf30bf10bfdb2e90399e0685d48a3ac8&type=album'
        }
      ]
    }
  },
  filters :{
    niceDate(value) {
      return date.formatDate(value, 'DD.MM.YYYY HH:mm:ss')
    }
  }
}
</script>

<style lang="sass">
  .card-post
    .q-img
      min-height: 200px
</style>