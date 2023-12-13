<template>
    <div>
        <form @submit.prevent="validarFormulario">
            <h2 class="text-primary">AYI-FORMULARIO</h2>
            <div v-if="errores.length!=0" class="alert alert-danger">
                {{ mostrarErrores }}
            </div>
            <!-- nombre -->
            <div class="forminput">
                <label>
                    Tu nombre:
                    <input type='text' v-model.trim="nombre" />
                    *
                </label>
                <!-- aqui parrafo para validar -->
                <p>Validar nombre: <span class="text-success fw-bold">{{ nombre }}</span></p>
            </div>
            <!-- Edad -->
            <div class="forminput">
                <label>
                    Edad:
                    <input type="number" v-model.number="edad">
                </label>
                <p>Validar edad: <span class="text-success fw-bold">{{ edad }}</span></p>
            </div>
            <!-- email -->
            <div class="forminput">
                <label>
                    Email:
                    <input type="text" v-model="email">
                    *
                </label>
                <p>Validar email: <span class="text-success fw-bold">{{ email }}</span></p>
            </div>
            <!-- Cursos -->
            <h5>Selecciona tu curso *</h5>
            <div class="formcheck">
                <label>
                    <input type="checkbox" value="JavaScript" v-model="cursos">
                    JavaScript
                </label>
                <label>
                    <input type="checkbox" value="Vue" v-model="cursos">
                    Vue
                </label>
                <label>
                    <input type="checkbox" value="HTML" v-model="cursos">
                    HTML
                </label>
                <label>
                    <input type="checkbox" value="CSS" v-model="cursos">
                    CSS
                </label>

            </div>
            <p>Validar cursos: <span class="text-success fw-bold">{{ cursos }}</span></p>
            <!-- comentarios -->
            <div class="formcheck">
                <label>
                    Comentarios
                    <input type="text" v-model.trim="comentarios">
                </label>

            </div>
            <p>Validar comentarios: <span class="text-success fw-bold">{{ comentarios }}</span></p>
            <!-- radio -->
            <h5>Tipo Documento</h5>
            <div class="formradio">
                <label>
                    <input type="radio" value="DNI" v-model="documento">
                    DNI
                </label>
                <label>
                    <input type="radio" value="Pasaporte" v-model="documento">
                    Pasaporte
                </label>
                <label>
                    <input type="radio" value="VISA" v-model="documento">
                    VISA
                </label>

            </div>
            <p>Validar documento: <span class="text-success fw-bold">{{ documento }}</span></p>
            <!-- selector -->
            <div class="formselect">
                <h5>País de origen</h5>
                <select v-model="pais">
                    <option value="" selected disabled>País</option>
                    <option value="Argentina">Argentina</option>
                    <option value="Chile">Chile</option>
                    <option value="Bolivia">Bolivia</option>
                </select>
                <p>Validar pais: <span class="text-success fw-bold">{{ pais }}</span></p>
            </div>
            <input class='btn btn-primary' type="submit" value="ENVIAR">
        </form>
    </div>
</template>

<script>
export default {
    name: 'FormularioComponent',

    data() {
        return {
            nombre: '',
            edad: null,
            email: '',
            cursos: [],
            documento: '',
            pais: '',
            comentarios: '',
            errores:[],
        };
    },

    methods: {
        validarFormulario(){
           /*  event.preventDefault(); */
           this.errores=[];
           if(this.nombre && this.email && this.cursos){
            alert('Los datos obligatorios fueron cargados, formulario enviado');
            //postear al servidor
            this.nombre='';
            this.edad=null;
            this.email='';
            this.cursos=[];
            this.documento='';
            this.pais='';
            this.comentarios='';
           }
           if(this.nombre == ''){
            this.errores.push('El nombre es un dato obligatorio');
           }
           if(this.email == ''){
            this.errores.push('El email es un dato obligatorio');
           }
           if(this.cursos.length == 0){
            this.errores.push('Incluir los cursos es un dato obligatorio');
           }
        }
    },
    computed: {
        mostrarErrores() {
            return this.errores.join(' - ');
        },
    
    },
};
</script>

<style scoped>
.formcheck,
.formradio {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding: 10px;
    margin: 10px;
}

.forminput,
.formselect {
    padding: 10px;
    margin: 10px;
}
</style>