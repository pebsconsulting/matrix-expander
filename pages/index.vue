<template>
  <main>
    <header class="flex flex-col items-center justify-center h-screen px-8">
      <h1 class="mb-8 text-6xl tracking-loose font-mono font-400 text-primary">
        Expand your Matrix
      </h1>

      <div class="flex flex-col">
        <call-to-action-primary
          class="btn btn-lg hover:btn-grow active:btn-pressed mb-6 bg-primary text-primary-700"
          :showIconBefore="true"
          component-id="cta-primary-landing-page"/>

        <nuxt-link
          class="btn btn-lg hover:btn-grow active:btn-pressed mb-6 border-2 border-primary-600 text-primary-600 hover:border-primary hover:text-primary"
          to="/docs">
          <div class="h-4 w-4 mr-2">
            <feather-book />
          </div>

          <span>Docs</span>
        </nuxt-link>

        <call-to-action-secondary
          class="btn btn-lg hover:btn-grow active:btn-pressed border-2 border-primary-600 text-primary-600 hover:border-primary hover:text-primary"
          :showIconBefore="false" />
      </div>
    </header>

    <section
      class="h-screen px-8 flex flex-col items-center justify-center"
      id="matrix-expander-ui-container">
      <matrix-expander-user-interface
        @edge-list-created="updateData"/>
    </section>

    <section
      class="h-screen py-16 px-8 flex flex-col items-center justify-center"
      id="edge-list-download-display-container">
      <edge-list-download-display
        class="flex-1"
        :edge-list="edgeList"
        :file-name="fileName" />
    </section>
  </main>
</template>

<script>
import FeatherBook from '~/components/icons/FeatherBook.vue'

import CallToActionPrimary from '~/components/CallToActionPrimary.vue'
import CallToActionSecondary from '~/components/CallToActionSecondary.vue'

import MatrixExpanderUserInterface from '~/components/MatrixExpanderUserInterface.vue'
import EdgeListDownloadDisplay from '~/components/EdgeListDownloadDisplay.vue'

export default {
  layout: 'master',
  components: {
    FeatherBook,
    CallToActionPrimary,
    CallToActionSecondary,
    MatrixExpanderUserInterface,
    EdgeListDownloadDisplay,
  },
  data () {
    return {
      edgeList: [],
      fileName: ''
    }
  },
  methods: {
    updateData (edgeList, fileName) {
      this.edgeList = edgeList
      this.fileName = fileName
    }
  }
}
</script>
