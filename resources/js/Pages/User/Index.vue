<template>
    <app-layout>
        <div>
            <inertia-link :href="route('users.create')">Cadastrar</inertia-link>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Nome</th>
                    <th>Email</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{user.name}}</td>
                    <td>{{user.email}}</td>
                    <td>
                        <inertia-link :href="route('users.edit',user.id)">Editar</inertia-link>
                        <button type="button" @click="excluir(user.id)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </app-layout>
</template>
<script>
import AppLayout from "../../Layouts/AppLayout"
export default {
    name:'Index',
    components:{AppLayout},
    props:{
        users: Object
    },
    methods:{
        excluir(id){
            console.log(id);
            this.$inertia.delete('/users/${id}')
        }
    }
}
</script>
<style scoped>

</style>
