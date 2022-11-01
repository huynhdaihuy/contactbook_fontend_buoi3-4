<template>
  <div class="page">
    <h4>Hiệu chỉnh Liên hệ</h4>
    <RegisterForm @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
  <script>
import RegisterForm from "../components/RegisterForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    RegisterForm,
  },
  props: {
    contact: { type: Object, default: null },
  },
  data() {
    return {
      message: "",
    };
  },
  methods: {
    async createContact(contact) {
      try {
        console.log(contact);
        await ContactService.create(contact);
        this.message = "Liên hệ được tạo thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
  create() {
    this.message = "";
  },
};
</script>  