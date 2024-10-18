<template>
    <BaseButton 
      :disabled="isPending" 
      :color="color"
      @click.stop.prevent="handleClick"
    >
      <template v-if="isPending">
        <FontAwesomeIcon :icon="['fas', 'circle-notch']" class="spinner" />
      </template>
      <template v-else>
        <slot></slot>
      </template>
    </BaseButton>
  </template>
  
  <script>
  import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
  import BaseButton from './BaseButton.vue';
  
  export default {
    name: 'AsyncButton',
    components: {
      BaseButton,
      FontAwesomeIcon
    },
    inheritAttrs: false,
    props: {
      color: {
        type: String,
        default: 'primary',
        validator: function(value) {
          return ['primary', 'warn', 'danger'].includes(value);
        }
      },
      disabled: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        isPending: false
      };
    },
    methods: {
      async handleClick() {
        if (this.isPending) return;
        this.isPending = true;
        try {
          await this.$emit('click'); 
        } finally {
          this.isPending = false;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .spinner {
    animation: spin 1s linear infinite; 
  }
  
  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
  
  
  </style>
  