<template>

<div class="container">
  
    <div>
        Bienvenido a Listar
    </div>
    <div class="card">
        <div class="card-header">
            Empleados
        </div>
        <div class="card-body">
            <table class="table">
                <thead>
                    <tr>
                         <th></th>
                        <th>ID</th>
                        <th>NOMBRE</th>
                        <th>CORREO</th>
                        <th>ACCIONES</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="empleado in empleados" :key= "empleado.id">
                        <td scope="row"></td>
                        <td>{{empleado.id}}</td>
                        <td>{{empleado.nombre}}</td>
                        <td>{{empleado.correo}}</td>
                        <td>
                            <a name="" id="" class="btn btn-primary" href="#" role="button"> Editar </a> | 
                            <a name="" id="" class="btn btn-primary" href="#" role="button"> Borrar </a> 
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
 </div>

</template>

<script>
export default {

    data(){
        return{
            empleados:[]
        }
    },

    created:function(){

        this.consultarEmpleados();

    },
    methods:{
        //http://localhost/empleados-main/
        consultarEmpleados(){
            fetch('http://localhost/empleados-main/')
            .then(respuesta => respuesta.json())
            .then((datosRespuesta) =>{
                console.log(datosRespuesta)
                this.empleados = []
                if(typeof datosRespuesta[0].succes === 'undefined'){
                    this.empleados = datosRespuesta;
                }

            })
            .catch(console.log)
        }

    }
    
}
</script>

<style scoped>

</style>