<template>
    <section>

<!-- Barra de navegacion -->
        <nav class="navbar navbar-light bg-dark justify-content-between">
            <a class="navbar-brand text-light">Bienvenido</a>
            <form class="form-inline">
                <button class="btn btn-outline-light me-2" type="button" @click="logOut"> Cerrar Sesión</button>
            </form>
        </nav>

        <div class="text-center mt-5">
            <h1>¡BIENVENIDO A HOME!</h1>
            <h4>Este sitio web está en construcción</h4>
        </div>

                <!-- carrusel -->
        <div class="container t-carrusel mt-3">
            <div class=" justify-content-center">
                <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
                    <div class="carousel-inner">
                        <div class="carousel-item active">
                            <img class="d-block w-100" src="https://placeimg.com/500/250/nature" alt="First slide">
                        </div>
                        <div class="carousel-item">
                            <img class="d-block w-100" src="https://placeimg.com/500/250/people" alt="Second slide">
                        </div>
                        <div class="carousel-item">
                            <img class="d-block w-100" src="https://placeimg.com/500/250/tech" alt="Third slide">
                        </div>
                    </div>
                    <a class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
                        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                        <span class="sr-only">Previous</span>
                    </a>
                    <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
                        <span class="carousel-control-next-icon" aria-hidden="true"></span>
                        <span class="sr-only">Next</span>
                    </a>
                    </div>
            </div>
        </div>
            <div class="d-flex justify-content-center">
                <img src="../assets/laTripleta.png" alt="" width="300" >
            </div>
    </section>
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
.t-carrusel{
    width: 500px;
    height: 250px;
}
.t-tripleta{
    display: block;
    margin-left: auto;
    margin-right: auto;
}
</style>