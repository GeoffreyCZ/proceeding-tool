<template>
  <Person title="Nezletilé dítě"></Person>
</template>

<script>
import Person from "@/components/Person";

export default {
  name: "Children",
  components: {Person},
  props: {
    title: {
      type: String,
      default: '',
    },
  },
}
</script>