<template>
  <div class="q-pa-md">
    <q-form @submit="ajouterObjectif" class="q-gutter-md">
      <q-input
        name="titre"
        v-model="titre"
        color="primary"
        label="Titre"
        filled
        clearable
      />

      <q-input
        name="competence"
        v-model="competence"
        color="primary"
        label="Quelle compétence souhaitez-vous acquérir ?"
        filled
        clearable
      />

      <q-select
        filled
        label="Niveau actuel"
        v-model="niveau"
        use-input
        hide-selected
        fill-input
        input-debounce="0"
        :options="niveaux"
      >
      </q-select>

      <calendrier></calendrier>

      <div class="row">
        <q-btn class="col" label="Ajouter" type="submit" color="primary" />
      </div>
    </q-form>

    <q-card v-if="objectifs.length > 0" flat bordered class="q-mt-md bg-grey-2">
      <q-separator />
      <q-card-section class="row q-gutter-sm items-center">
        <div
          v-for="(objectif, index) in objectifs"
          :key="index"
          class="q-px-sm q-py-xs bg-grey-8 text-white rounded-borders text-center text-no-wrap"
        >
          {{ objectif.titre }} - {{ objectif.competence }}
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
import Calendrier from "./Calendrier.vue";
export default {
  components: {
    Calendrier
  },
  data() {
    return {
      titre: "",
      competence: "",
      niveau: "",
      date: "",
      objectifs: [],
      accepted: [],

      niveaux: [
        {
          label: "Débutant",
          value: "debutant"
        },
        {
          label: "Moyen",
          value: "moyen"
        },
        {
          label: "Confirmé",
          value: "confirme"
        },
        {
          label: "Expert",
          value: "expert"
        }
      ]
    };
  },
  methods: {
    ajouterObjectif(evt) {
      const form = new FormData(evt.target);
      const objectifs = [];

      for (const [titre, competence, niveau] of form.entries()) {
        objectifs.push({
          titre,
          competence,
          niveau
        });
      }
      this.objectifs = objectifs;
    }
  }
};
</script>

<style>
</style>
