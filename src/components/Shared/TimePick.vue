<template>
  <div>
    <v-layout row>
      <v-flex xs12 sm6 offset-sm3>
        <h4>Choose a Data & Time</h4>
      </v-flex>
    </v-layout>
    <v-layout row class="mb-2">
      <v-flex xs12 sm6 offset-sm3>
        <v-date-picker v-model="date"></v-date-picker>
      </v-flex>
    </v-layout>
  </div>
</template>
