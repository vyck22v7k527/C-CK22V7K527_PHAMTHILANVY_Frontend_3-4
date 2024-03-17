<template>
    <div class="page">
        <h4>Thêm mới Liên hệ</h4>
        <ContactForm :contact="newContact" @submit:contact="createContact" />
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
            newContact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false
            }
        };
    },
    methods: {
        // createContact(contact) {
        //      Logic để thêm mới liên hệ

        // }
        // 
        async createContact(data) {
            try {
                await ContactService.create(data);
                alert("Thêm thành công!");
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.error(error);
            }
        },
        // cancel() {
        //     this.$router.push({ name: "contactbook" });
        // }
    },
};
</script>
