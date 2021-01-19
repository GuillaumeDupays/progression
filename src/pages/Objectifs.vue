<template>
  <div class="q-pa-md">
    <q-layout
      view="lHh lpr lFf"
    >
      <q-header elevated> </q-header>

      <q-page-container>
        <q-page padding>
          <h4>Fixez vos objectifs</h4>

            <add-objectif></add-objectif>
            <liste-objectifs></liste-objectifs>

        </q-page>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
import AddObjectif from "src/components/AddObjectif.vue";
import ListeObjectifs from "src/components/ListeObjectifs.vue";

export default {
  components: {
    AddObjectif,
    ListeObjectifs
  }
};
</script>

<style></style>
