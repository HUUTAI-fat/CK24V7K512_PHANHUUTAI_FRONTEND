<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm 
            :contact="contact" 
            @submit:contact="addContact"
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
            // Khởi tạo một đối tượng contact rỗng để truyền vào Form
            contact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false,
                favoriteNote: "", // Thêm dòng này
                hobbies: []       // Thêm dòng này
            },
            message: "",
        };
    },
    methods: {
        async addContact(data) {
            try {
                // Gọi API để thêm mới liên hệ
                await ContactService.create(data);
                alert('Liên hệ được thêm thành công.');
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>