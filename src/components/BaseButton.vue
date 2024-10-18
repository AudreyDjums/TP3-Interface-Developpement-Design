<template>
    <button 
      class="base-button"
      :class="[colorClass, { 'base-button--disabled': disabled }]"
      :style="style"
      :disabled="disabled"
      @click="handleClick"
    >
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    name: 'BaseButton',
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
      },
      style: {
        type: Object,
        default: () => ({})
      },
      handleClick: {
        type: Function,
        default: () => {}
      }
    },
    computed: {
      colorClass() {
        return `base-button--${this.color}`;
      }
    }
  };
  </script>
  
  <style scoped>
  .base-button {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    outline: none;
    transition: all 0.3s ease;
  }
  
  .base-button--primary {
    color: white;
    background-color: #4caf50;
  }
  
  .base-button--warn {
    color: white;
    background-color: #ff9800;
  }
  
  .base-button--danger {
    color: white;
    background-color: #f44336;
  }
  
  .base-button:hover:not(.base-button--disabled) {
    filter: brightness(0.9);
  }
  
  .base-button:focus {
    box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.5);
  }
  
  .base-button:active:not(.base-button--disabled) {
    transform: scale(0.98);
  }
  
  .base-button--disabled {
    background-color: #b0b0b0;
    cursor: not-allowed;
    color: #ffffff;
  }
  </style>
  