<template>
    <div clas="row">
        <div class="col-lg-8 offset-lg-2">
            <div class="table-responsive">
                <table class="table table-bordered table-hover">
                    <thead>
                        <tr>
                            <th>#</th>
                            <th>TipoCargo</th>
                            <th>Estado</th>
                        </tr>
                    </thead>
                    <tbody class="table-group-divider" id="contenido">
                        <tr v-for="prod, i, in products" :key="prod.idCargo">
                            <td>{{ (i+1) }}</td>
                            <td>{{ prod.tipoCargo }}</td>
                            <td>{{ prod.estado }}</td>
                        </tr>
                    </tbody>
                </table>

            </div>
        </div>
    </div>
</template>

<script>

import axios from 'axios';

export default {
    data() {
        return { products: null }
    },
    mounted() {
        this.getProducts();

    },
    methods: {
        getProducts() {
            
            axios.get('api/listCargo').then(
                response => (
                    this.products = response.data
                   
                )

            );
        }
    }

}


</script>