<template>
    <div class="container text-center">
      <h2 class="text-danger">Hapus Donasi</h2>
      <p>Apakah Anda yakin ingin menghapus donasi ini?</p>
      <button @click="deleteProject" class="btn btn-danger">Ya, Hapus</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['projectId'],
    methods: {
      async deleteProject() {
        try {
          await fetch(`/donation/${this.projectId}`, { method: 'DELETE' });
          this.$emit('deleted');
        } catch (error) {
          console.error('Error deleting donation:', error);
        }
      }
    }
  };
  </script>
  