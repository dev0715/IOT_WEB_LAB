<template>
  <section id="service_list">
    <v-row no-gutters>
      <v-col cols="12">
        <v-container class="py-8">
          <h3
            class="text-uppercase text-h6 text-md-h5 text-center font-weight-black ma-16"
          >
            {{ $t('sections.blockchainTechnologies.title') }}
          </h3>
          <v-row class="my-5">
            <v-col
              v-for="tech in technologies"
              :key="tech.name"
              cols="4"
              sm="2"
              xl="1"
              class="font-weight-black py-2"
            >
              <a
                :href="tech.link"
                target="_blank"
                :class="
                  $vuetify.theme.dark
                    ? 'grey--text text--lighten-2'
                    : 'grey--text text--darken-2'
                "
              >
                <div class="d-flex flex-column">
                  <div class="custom__item">
                    <SimpleSVG
                      :src="tech.icon"
                      :width="size"
                      :height="size"
                      fill-class-name="fill-to-change"
                      :custom-id="tech.name"
                      :fill="$vuetify.theme.dark ? '#FBFBFB' : '#454545'"
                      :stroke="$vuetify.theme.dark ? '#FBFBFB' : '#454545'"
                    />
                  </div>
                  <h6
                    class="text-uppercase text-center mt-1 mb-4"
                    style="letter-spacing: 0.15em"
                    v-text="tech.name"
                  ></h6>
                </div>
              </a>
            </v-col>
          </v-row> </v-container
      ></v-col>
    </v-row>
  </section>
</template>
<script>
import { SimpleSVG } from 'vue-simple-svg'
import { mapGetters } from 'vuex'
export default {
  components: {
    SimpleSVG,
  },
  data() {
    return {
      size: '60px',
    }
  },
  computed: {
    ...mapGetters({
      technologies: 'blockchain/technologies',
    }),
  },
}
</script>
<style scoped>
a {
  text-decoration: none;
}
.custom__item {
  width: fit-content;
  justify-self: center;
  align-self: center;
}
</style>
