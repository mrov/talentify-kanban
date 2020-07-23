<template>
  <v-app>
    <v-container>
      <v-row no-gutters>
        <kanbanColumn/>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import kanbanColumn from '@/components/kanbanColumn'

export default {
  name: 'App',
  components: {
    kanbanColumn
  }
}
</script>

<style>
* {
  margin: 0px;
}
#app {
  background-color: darkblue;
  width: 100%;
  min-height: 100vh;
}
.w-100 {
  width: 100%;
}
.pointer {
  cursor: pointer;
}
</style>
