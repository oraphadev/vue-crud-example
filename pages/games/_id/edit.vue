<template>
  <div class="game-edit">
    <FormWrapperSkeleton v-if="loading" />

    <FormWrapper
      ref="formWrapper"
      v-else
      :game="game"
      @submit="handleSubmit"
    />
  </div>
</template>

<script>
import axios from 'axios';
import FormWrapper from '@/components/Game/FormWrapper';
import FormWrapperSkeleton from '@/components/Game/FormWrapperSkeleton';

export default {
  name: 'GamesEdit',

  components: {
    FormWrapper,
    FormWrapperSkeleton,
  },
  
  data: () => ({
    loading: false,
    game: {
      name: '',
      slug: '',
    },
  }),

  mounted() {
    await this.loadGame();
  },

  methods: {
    async loadGame() {
      this.loading = true;

      try {
        const { data } = axios.create({
          method: 'PUT',
          url: `/games/${this.$route.params.id}`,
          data: game,
        });

        this.game = data;
      } catch (err) {
        console.warn(err);
      } finally {
        this.loading = false;
      }
    },

    handleSubmit() {
      axios.create({
        method: 'PUT',
        url: `/games/${this.$route.params.id}`,
        data: game,
      });
    },
  }
};
</script>
