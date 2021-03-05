<template>
  <v-row align="center" justify="center">
    <v-col cols="12" sm="6">
      <v-card
          class="pa-5 text-center"
          raised
          tile
      >
        <v-select
            v-model="proceedingType"
            :items="typeOptions"
            label="Návrh"
            outlined
        >
        </v-select>

        <div v-if="proceedingType === 1">
          <Determination/>
        </div>
        <div v-if="proceedingType === 2">
          <Increase/>
        </div>
        <div v-if="proceedingType === 3">
          <Decrease/>
        </div>
        <div v-if="proceedingType === 4">
          <Change/>
        </div>
        <div v-if="proceedingType === 5">
          <Edit/>
        </div>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Determination from './Determination';
import Increase from "@/components/Increase";
import Decrease from "@/components/Decrease";
import Change from "@/components/Change";
import Edit from "@/components/Edit";

export default {
  name: 'Form',

  components: {
    Edit,
    Change,
    Decrease,
    Increase,
    Determination,
  },
  data: () => ({
    proceedingType: '',
    typeOptions: [
      {
        'value': 1,
        'text': 'O svěření nezletilého dítěte do péče a určení výživného'
      },
      {
        'value': 2,
        'text': 'O zvýšení výživného'
      },
      {
        'value': 3,
        'text': 'O snížení výživného'
      },
      {
        'value': 4,
        'text': 'O změně péče'
      },
      {
        'value': 5,
        'text': 'O úpravě styku'
      }
    ]
  }),
}
</script>