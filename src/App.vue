<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <fetch-json url="https://randomuser.me/api/?results=10">
        <div class="card" slot-scope="{json }">
          <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
          <div>
            <div v-for="contact in json" :key="contact.id" class="flex items-center spaced-y-6">
              <img :src="contact.picture.medium" class="h-12 w-12 rounded-full block mr-2" alt="">
              <div>
                <div class="font-bold">
                  {{ contact.name.first }} {{ contact.name.last }}
                </div>
                <div class="text-grey-dark">
                  {{ contact.email }}
                </div>
              </div>
            </div>
          </div>
        </div>
      </fetch-json>

    </div>
  </div>

</template>

<script>
import FetchJson from "./components/FetchJson.vue"
export default {
  name: "App",
  components: {
    FetchJson
  }
}
</script>

<style src="./assets/css/app.css"/>
