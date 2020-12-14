<template>
    <div>
        <nav class="navbar navbar-light bg-light">
            <form class="container-fluid justify-content-end">
                <button class="btn btn-outline-success me-2" 
                type="button"
                @click="logOut"
                >Cerrar Sesión</button>
            </form>
        </nav>
        <div>
            <p>La lógica {{user.nombre}}</p>
            <p>{{user.email}}</p>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            user:{}

        }
    },
    methods:{
        getUserDetails(){
            let user = localStorage.getItem('user');
            let token = localStorage.getItem('jwt');

            if(token){
                this.user = JSON.parse(user);
            }
        },
// metodo para cerrar secion
        logOut(){
            localStorage.removeItem('jwt');
            localStorage.removeItem('user');
            this.$router.push('/');
        }
    },
    created(){
        this.getUserDetails();
    }   
}
</script>

<style scoped>

</style>