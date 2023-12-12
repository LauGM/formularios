<template>
    <div>
        <form>
            <h2 class="text-primary">AYI-FORMULARIO</h2>
            <!-- nombre -->
            <div class="forminput">
                <label>
                    Tu nombre:
                    <input type='text' v-model="nombre" />
                </label>
                <!-- aqui parrafo para validar -->
                <p>Validar nombre: <span class="text-success fw-bold">{{ nombre }}</span></p>
            </div>
            <!-- Edad -->
            <div class="forminput">
                <label>
                    Edad:
                    <input type="text">
                </label>
            </div>
            <!-- email -->
            <div class="forminput">
                <label>
                    Email:
                    <input type="text">
                </label>
            </div>
            <!-- Cursos -->
            <h5>Selecciona tu curso</h5>
            <div class="formcheck">
                <label>
                    <input type="checkbox" value="">
                    JavaScript
                </label>
                <label>
                    <input type="checkbox" value="">
                    Vue
                </label>
                <label>
                    <input type="checkbox" value="">
                    HTML
                </label>
                <label>
                    <input type="checkbox" value="">
                    CSS
                </label>
            </div>
            <!-- comentarios -->
            <div class="formcheck">
                <label>
                    Comentarios
                    <input type="text">
                </label>
            </div>
            <!-- radio -->
            <h5>Tipo Documento</h5>
            <div class="formradio">
                <label>
                    <input type="radio" value="">
                    DNI
                </label>
                <label>
                    <input type="radio" value="">
                    Pasaporte
                </label>
                <label>
                    <input type="radio" value="">
                    VISA
                </label>
            </div>
            <!-- selector -->
            <div class="formselect">
                <h5>País de origen</h5>
                <select>
                    <option value="" selected disabled>País</option>
                    <option value="">Argentina</option>
                    <option value="">Chile</option>
                    <option value="">Bolivia</option>
                </select>
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
            nombre:'',
        };
    },

    methods: {

    },
};
</script>

<style scoped>
.formcheck, .formradio {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding: 10px;
}

.forminput, .formselect{
    padding:10px;
}
</style>