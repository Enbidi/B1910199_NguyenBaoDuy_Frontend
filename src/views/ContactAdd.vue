<script>
import ContactForm from '@/components/ContactForm.vue'
import ContactService from '@/services/contact.service'

export default {
    components: {
        ContactForm
    },
    data() {
        return {
            message: ''
        }
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data)
                this.message = 'Liên hệ được cập nhật thành công'
            } catch(error) {
                console.log(error)
            }
        }
    },
    created() {
        this.message = ''
    }
}
</script>

<template>
    <h4>Thêm liên hệ liên hệ</h4>
    <ContactForm 
        :contact="{}"
        @submit:contact="addContact"
        :edit="false"
    />
    <p>{{ message }}</p>
</template>