<template>
  <v-card color="black" dark flat tile>
    <v-window v-model="onboarding" :touch="{left: next, right: prev}">
      <v-window-item v-for="(txt, n) in text" :key="n">
        <v-card color="transparent" height="812px" width="375px">
          <v-row class="fill-height" align="end" justify="center">
            <v-card-text class="text-center">
              <h3>{{ txt.title}}</h3>
              <p>{{ txt.text}}</p>
            </v-card-text>
          </v-row>
        </v-card>
      </v-window-item>
    </v-window>

    <v-card-actions class="justify-space-between">
      <v-btn text @click="prev">
        SKIP
        <!-- <v-icon>mdi-chevron-left</v-icon> -->
      </v-btn>
      <v-item-group v-model="onboarding" class="text-center" mandatory>
        <v-item
          v-for="n in length"
          :key="`btn-${n}`"
          v-slot="{ active, toggle }"
        >
          <v-btn :input-value="active" icon @click="toggle">
            <v-icon small>mdi-record</v-icon>
          </v-btn>
        </v-item>
      </v-item-group>
      <v-btn text @click="next">
        NEXT
        <!-- <v-icon>mdi-chevron-right</v-icon> -->
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    length: 4,
    onboarding: 0,
    text: [
      {
        title: 'Select your game',
        text: 'Cricket, football or tennis.',
      },
      {
        title: 'Predict in Match',
      },
      {
        title: 'Create your own Team',
      },
      {
        title: 'Play with Friends',
      },
    ],
  }),

  methods: {
    next() {
      this.onboarding =
        this.onboarding + 1 === this.length ? 0 : this.onboarding + 1
    },
    prev() {
      this.onboarding =
        this.onboarding - 1 < 0 ? this.length - 1 : this.onboarding - 1
    },
  },
}
</script>