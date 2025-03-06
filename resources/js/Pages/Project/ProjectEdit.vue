<template>
    <div>
        <div class="container mt-5">
            <h2 class="text-center">Edit Donasi</h2>
            <form @submit.prevent="submitForm">
                <div class="form group">
                    <label for="content">Nama</label>
                    <input v-model="form.title" type="text" class="form-control">
                </div>
                <div class="form group">
                    <label for="content">Deskripsi</label>
                    <input v-model="form.description" type="text" class="form-control">
                </div>
                <div class="form group">
                    <label for="content">Target</label>
                    <input v-model="form.target_amount" type="text" class="form-control">
                </div>

                <button type='submit' class="btn btn-primary mt-5">Simpan</button>

            </form>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        project: Object
    },
  data() {
    return {
        form: {
            title: this.project.title,
            description: this.project.description,
            target_amount: this.project.target_amount,
        }
    }
  },

  methods: {
    submitForm() {
        this.$inertia.put(`/donation/${this.project.id}`, this.form);
    }
  }
}
</script>