<template>
  <v-card class="max-auto" max-width="300" tile>
    <v-list rounded>
      <v-subheader>Cart</v-subheader>
      <v-list-item-group v-model="item" color="primary">
        <v-list-item v-for="(item, i) in items" :key="i">
          <v-card class="mx-2">
            <v-img :src="item.src" class="white--text align-end" height="50px" width="50px"></v-img>
          </v-card>
          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      item: 1,
      items: [
        {
          text: "Real-Time",
          src:
            "https://images.unsplash.com/photo-1581184953963-d15972933db1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=574&q=80"
        },
        {
          text: "Audience",
          src:
            "https://images.unsplash.com/photo-1581184953963-d15972933db1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=574&q=80"
        },
        {
          text: "Conversions",
          src:
            "https://images.unsplash.com/photo-1581184953963-d15972933db1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=574&q=80"
        }
      ]
    };
  }
};
</script>

<style>
</style>