<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6" v-for="n in 9" :key="n">
      <bubble></bubble>
    </v-col>
  </v-row>
</template>

<script>
export default {
}
</script>
