<template>
  <div>
    <v-select
        v-model="proposer"
        :items="proposerOptions"
        label="Navrhovatel"
        outlined
    >
    </v-select>
    <Children
        v-for="(child, index) in children"
        :key="index"
        :is="child"
    />
    <v-btn
        elevation="2"
        outlined
        @click="add"
    >Přidat dítě
    </v-btn>
    <Person title="Matka"/>
    <Person title="Otec"/>
    <Person title="Navrhovatel" v-if="proposer === 'Jiná osoba'"/>
    <v-textarea
        outlined
        name="input-7-4"
        label="Zdůvodnění"
    ></v-textarea>
    <v-select
        v-model="carer"
        :items="carerOptions"
        label="Komu by dítě mělo být svěřeno"
        outlined
    ></v-select>
    <v-text-field
        v-if="carer === 'Matce'"
        label="V jaké výši by mělo být výživné stanoveno otci"
        outlined/>
    <v-text-field
        v-else-if="carer === 'Otci'"
        label="V jaké výši by mělo být výživné stanoveno matce"
        outlined/>
    <div v-else-if="carer === 'Jiné osobě'">
      <v-text-field
          label="V jaké výši by mělo být výživné stanoveno matce"
          outlined/>
      <v-text-field
          label="V jaké výši by mělo být výživné stanoveno otci"
          outlined/>
    </div>
  </div>
</template>

<script>
import Person from "@/components/Person";
import Children from "@/components/Children";

export default {
  name: "Determination",

  components: {Children, Person},

  data: () => ({
    proposer: '',
    proposerOptions: ['Matka', 'Otec', 'Jiná osoba'],
    carer: '',
    carerOptions: ['Matce', 'Otci', 'Jiné osobě'],
    children: [Children],
  }),

  methods: {
    add() {
      this.children.push(Children)
    }
  }
}
</script>

<style scoped>

</style>