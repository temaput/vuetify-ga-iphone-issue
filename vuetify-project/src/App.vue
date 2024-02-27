<template>
  <v-defaults-provider :defaults="defaults">
    <v-app>
      <v-main>
        <v-row class="d-flex align-center justify-center">
          <v-col cols="auto">
            <div class="ma-4">
              <v-btn variant="text" @click.stop="handle">
                Click Me (Component)
              </v-btn>
            </div>

            <div class="ma-4">
              <button type="button"
                class="v-btn v-theme--light v-btn--density-default v-btn--size-default v-btn--variant-text"
                @click.stop="handle">
                <span class="v-btn__overlay"></span><span class="v-btn__underlay"></span><!----><span
                  class="v-btn__content" data-no-activator="">Click Me (Plain HTML)</span><!----><!---->
              </button>
            </div>
            <div class="ma-4">
              <button type="button"
                class="v-btn v-theme--light v-btn--density-default v-btn--size-default v-btn--variant-text"
                @click.stop="handle">
                <span class="v-btn__underlay"></span><!----><span class="v-btn__content" data-no-activator="">Click Me
                  (No overlay)</span><!----><!---->
              </button>

            </div>
          </v-col>
        </v-row>

      </v-main>
    </v-app>
  </v-defaults-provider>
</template>

<script setup>
import { computed } from 'vue';
import { useDisplay } from 'vuetify/lib/framework.mjs';

const { mobile, platform,  } = useDisplay()


console.log("Platform: ", platform.value)

const defaults = computed(() => platform.value.ios || platform.value.android ? {} : {

  global: {
    ripple: false,
  }


})
const defaultsStatic = {

  global: {
    ripple: false,
  }


}
const handle = () => {
  alert("Fire!")
}
</script>

<style>
.v-btn:hover>.v-btn__overlay {
  opacity: 0 !important;
}

.v-btn>.v-btn__overlay {
  opacity: 0 !important;
}

@media (pointer: fine) {
  .v-btn:hover>.v-btn__overlay {
    opacity: 0.2 !important;
  }
}
</style>
