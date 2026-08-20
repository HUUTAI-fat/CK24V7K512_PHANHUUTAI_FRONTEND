<template>
    <nav class="navbar navbar-expand navbar-dark bg-dark">
        <a href="/" class="navbar-brand">Ứng dụng Quản lý danh bạ</a>
        <div class="mr-auto navbar-nav">
            <li class="nav-item">
                <router-link :to="{ name: 'contactbook' }" class="nav-link">
                    Danh bạ
                    <i class="fas fa-address-book"></i>
                </router-link>
            </li>
        </div>
        
        <!-- Phần thêm mới cho Đăng nhập -->
        <div class="navbar-nav ml-auto">
            <li class="nav-item" v-if="!currentUser">
                <router-link :to="{ name: 'login' }" class="nav-link">
                    Đăng nhập <i class="fas fa-sign-in-alt"></i>
                </router-link>
            </li>
            <li class="nav-item" v-else>
                <span class="nav-link text-white">Xin chào, {{ currentUser }}!</span>
            </li>
            <li class="nav-item" v-if="currentUser">
                <a class="nav-link" style="cursor: pointer;" @click="logout">
                    Đăng xuất <i class="fas fa-sign-out-alt"></i>
                </a>
            </li>
        </div>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            currentUser: null,
        };
    },
    created() {
        this.currentUser = localStorage.getItem("user");
    },
    methods: {
        logout() {
            localStorage.removeItem("user");
            this.currentUser = null;
            this.$router.push({ name: "login" });
        }
    }
};
</script>