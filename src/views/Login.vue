<template>
    <div class="page mt-4">
        <h4 class="text-center">Đăng nhập</h4>
        <form @submit.prevent="handleLogin">
            <div class="form-group">
                <label>Tên đăng nhập</label>
                <input type="text" class="form-control" v-model="username" required />
            </div>
            <div class="form-group">
                <label>Mật khẩu</label>
                <input type="password" class="form-control" v-model="password" required />
            </div>
            <button type="submit" class="btn btn-primary btn-block">Đăng nhập</button>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: "",
            password: "",
        };
    },
    methods: {
        handleLogin() {
            // Đăng nhập giả lập: Lưu tên user vào trình duyệt
            if (this.username && this.password) {
                localStorage.setItem("user", this.username);
                this.$router.push({ name: "contactbook" }).then(() => {
                    window.location.reload(); // Tải lại để Header cập nhật
                });
            }
        },
    },
};
</script>