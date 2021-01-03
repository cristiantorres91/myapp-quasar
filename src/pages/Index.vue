<template>
  <q-page class="q-pa-md">
    <!-- componente listview quasar -->
    <q-list bordered padding>
      <q-item-label header>Users</q-item-label>
      <div v-for="item in dataApi" :key="item.id">
        <q-item>
          <q-item-section top avatar>
            <q-icon
              name="account_circle"
              class="text-secondary"
              style="font-size: 30px"
            />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ item.name }}</q-item-label>
            <q-item-label caption>{{ item.email }}</q-item-label>
          </q-item-section>
        </q-item>
        <q-separator spaced inset="item" />
      </div>
    </q-list>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",

  data() {
    return {
      dataApi: [],
    };
  },
  async mounted() {
    this.getData();
  },
  methods: {
    async getData() {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        this.dataApi = await response.json();
        console.log(this.dataApi);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
