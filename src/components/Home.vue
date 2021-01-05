<template>
    <div class="">
        <table>
            <tr>
                <td>Id</td>
                <td>Name</td>
                <td>Email</td>
            </tr>
            <tr v-for="item in list" v-bind:key="item.id">
                <td>{{item.id}}</td>
                <td>{{item.name}}</td>
                <td>{{item.email}}</td>
            </tr>
        </table>

    </div>
</template>
<script>
import Vue from 'vue';
import axios from 'axios';
import VueAxios from 'vue-axios';
Vue.use(VueAxios, axios)
export default {
    name: "Home",
    data() {
        return {list: undefined}
    },
    mounted() {
        Vue.axios.get('https://jsonplaceholder.typicode.com/users')
        .then((res)=>{
            this.list = res.data
            console.log(res.data)
        })
    }
}
</script>