<template>
    <div class="page">
      <h4>Thêm mới Liên hệ</h4>
      <ContactFormAdd @submit:contact="addContact" />
      <p>{{ message }}</p>
    </div>
  </template>
  
  <script>
  import ContactFormAdd from "@/components/ContactFormAdd.vue";
  import ContactService from "@/services/contact.service";
  
  export default {
    components: {
      ContactFormAdd,
    },
    data() {
      return {
        message: "",
      };
    },
    methods: {
      async addContact(contactData) {
        try {
          await ContactService.create(contactData);
          this.message = "Liên hệ được thêm thành công.";
        } catch (error) {
          console.error("Error adding contact:", error);
          this.message = "Có lỗi xảy ra khi thêm liên hệ.";
        }
      },
    },
  };
  </script>
  