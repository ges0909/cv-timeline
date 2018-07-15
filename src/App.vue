<template>
  <div id="app">
    <CvTimeline>

      <CvEntry from="12/2017" to="heute" client="infinIT services GmbH" link="https://infinit-services.de/">
        Entwicklung eines Web-Portals für ein Energie-Management-System
      </CvEntry>

      <CvEntry from="05/2017" to="11/2017" client="Schufa Holding AG" link="https://www.schufa.de/de/">
        Wartung und Weiterentwicklung eines Systems zum Risikomanagement
      </CvEntry>

      <CvEntry from="03/2017" to="05/2017" client="infinIT services GmbH" link="https://infinit-services.de/">
        Entwicklung eines IoT-Simulators
      </CvEntry>

      <CvEntry from="01/2017" to="03/2017" client="ERGO Direkt Versicherungen" link="https://ergodirekt.de/de.html">
        Entwicklung einer REST-Schnittstelle für eine Versicherung
      </CvEntry>

      <CvEntry from="09/2016" to="12/2016" client="infinIT services GmbH" link="https://infinit-services.de/">
        Entwicklung eines Web-Portals für den Energie-Sektor
      </CvEntry>

    </CvTimeline>
  </div>
</template>

<script>
import CvTimeline from '@/components/CvTimeline.vue'
import CvEntry from '@/components/CvEntry.vue'

export default {
  name: 'app',
  components: {
    CvTimeline,
    CvEntry
  }
}
</script>

<style>
/* #app {
} */
</style>
