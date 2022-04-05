<template>
  <form @submit.prevent="handleSubmit">
    <div class="form-item">
      <NameInput v-model="game.name" />
    </div>

    <div class="form-item">
      <SlugInput v-model="game.slug" />
    </div>
  </form>
</template>

<script>
// Componentes fake que vão manipular os dados através do v-model
import NameInput from '@/components/Game/NameInput';
import SlugInput from '@/components/Game/SlugInput';

export default {
  name: 'GameFormWrapper',

  components: {
    NameInput,
  },

  props: {
    game: {
      type: Object,
      required: true,
    },
  },

  methods: {
    handleSubmit() {
      this.$emit('submit');
    },
  },
};
</script>
