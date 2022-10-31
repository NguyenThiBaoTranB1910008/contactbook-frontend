<template>
    <div v-if="contact" class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="createContact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        async createContact(contact) {
            try {
                console.log(contact);
                await ContactService.create(this.contact);
                this.message = "Liên hệ đã được thêm mới.";
            } catch (error) {
                console.log(error);
            }
        },

    },
};
</script>

    