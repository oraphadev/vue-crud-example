<template>
  <div class="game-create">
    <FormWrapper
      ref="formWrapper"
      :game="game"
      @submit="handleSubmit"
    />
  </div>
</template>

<script>
import axios from 'axios';
import FormWrapper from '@/components/Game/FormWrapper';

export default {
  name: 'GamesCreate',

  components: {
    FormWrapper,
  },
  
  data: () => ({
    game: {
      name: '',
      slug: '',
    },
  }),

  methods: {
    handleSubmit() {
      axios.create({
        method: 'POST',
        url: '/games',
        data: game,
      });
    },
  }
};
</script>
