<template>
  <!-- <v-sheet outlined rounded color="white"> -->
    <v-card outlined flat>
      <div v-if="$slots.title || $slots.subtitle" class="card-top">
        <v-card-title v-if="$slots.title" class="title-text">
          <slot name="title"></slot>
        </v-card-title>

        <v-card-subtitle v-if="$slots.subtitle" class="text-caption font-weight-bold">
          <slot name="subtitle"></slot>
        </v-card-subtitle>
      </div>

      <v-divider v-if="$slots.title || $slots.subtitle"></v-divider>

      <v-card-text v-if="$slots.defaultContent" class="black--text content-text card-content">
        <slot name="defaultContent"></slot>
      </v-card-text>

      <slot></slot>
    </v-card>
  <!-- </v-sheet> -->
</template>


<style scoped>
.card-top {
  padding: 10px
}

.card-content {
  padding: 25px;
}
</style>
