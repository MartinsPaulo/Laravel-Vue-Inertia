<template>
    <app-layout>
        <div>
            <form @submit.prevent="submit">
                <div>
                    <label for="name">Nome</label>
                    <input type="text" id="name" v-model="form.name">
                    <div v-show="errors.name">{{errors.name}}</div>
                </div>
                <div>
                    <label for="email">Email</label>
                    <input type="text" id="email" v-model="form.email">
                    <div v-show="errors.email">{{errors.email}}</div>
                </div>
                <div>
                    <label for="password">Senha</label>
                    <input type="password" id="password" v-model="form.password">
                    <div v-show="errors.password">{{errors.password}}</div>
                </div>
                <button>Cadastrar</button>
            </form>
        </div>
    </app-layout>
</template>
<script>
import AppLayout from "../../Layouts/AppLayout"
export default {
    name:'Create',
    components:{AppLayout},
    props:{
        errors: Object
    },
    data(){
        return{
            form:{
                name:null,
                email:null,
                password:null
            }
        }
    },
    methods:{
        submit(){
            this.$inertia.post('/users',this.form);

            this.form = {
                name:null,
                email:null,
                password:null
            }

        }
    }
}
</script>
<style scoped>

</style>
