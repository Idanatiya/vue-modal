<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot> Default content </slot>
      <div v-if="$slots.links" class="actions">
        <slot name="links" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme"],
  methods: {
    closeModal() {
      //this is how we emit a custom event from child to parent
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal {
  min-width: 350px;
  width: fit-content;
  padding: 20px;
  margin: 100px auto;
  background: #fff;
  border-radius: 5px;
}

.backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  text-decoration: none;
  border-radius: 4px;
  color: #333;
  border: 1px solid #eee;
  padding: 8px;
  margin: 10px;
}

.modal.sale {
  background-color: crimson;
  color: white;
}

.modal.sale .actions {
  color: white;
}

.modal.sale .actions a {
  color: white;
}
</style>
