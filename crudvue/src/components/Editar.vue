<template>

<div>

    <div class="container">
        <div class="card">
            <div class="card-header">
                Editar Empleado
            </div>
            <div class="card-body">

                <form v-on:submit.prevent="actualizarRegistro">

                    <div class="form-group">
                      <label for="nombre">Nombre:</label>
                      <input type="text"
                        class="form-control" required name="nombre" id="nombre" v-model="empleado.nombre" aria-describedby="helpId" placeholder="Nombre">
                      <small id="helpId" class="form-text text-muted">Nombre nuevo empleado</small>
                    </div>

                    <div class="form-group">
                      <label for="correo">Correo</label>
                      <input type="email"
                        class="form-control" required name="correo" id="correo" v-model="empleado.correo" aria-describedby="helpId" placeholder="Correo">
                      <small id="helpId" class="form-text text-muted">Ingrese el correo electronico</small>
                    </div>

                    <div class="btn-group" role="group" aria-label="">
                        <button type="submit" class="btn btn-success">Modificar</button> 
                        <router-link :to="{name: 'Listar'}" class="btn btn-warning">Cancelar</router-link>

                    </div>

                </form>

            </div>

        </div>
    </div>
</div>

</template>

<script>
export default {
     data(){

        return{

            empleado: {}

        }

    },
    created:function(){
        this.obtenerInfo();
    },

    methods:{
        obtenerInfo(){
          
            fetch('http://localhost/empleados-main/?consultar='+this.$route.params.id)
            .then(respuesta => respuesta.json())
            .then((datosRespuesta) =>{
                console.log(datosRespuesta)
                this.empleado = datosRespuesta[0];
            })
            .catch(console.log)
        },
        actualizarRegistro(){

            var datosEnviar = {id:this.$route.params.id,nombre:this.empleado.nombre, correo:this.empleado.correo};

            fetch('http://localhost/empleados-main/?actualizar='+this.$route.params.id,{
                method:"POST",
                body:JSON.stringify(datosEnviar)
            })
            .then(respuesta => respuesta.json())
            .then((datosRespuesta => {
                console.log(datosRespuesta);
                window.location.href='../listar'
            }))

        }
    }
}
</script>

<style scoped>

</style>