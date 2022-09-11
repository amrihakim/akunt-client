<template>
    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-8">
                <div class="card rounded shadow mb-3">
                    <div class="card-body">
                        <div class="row text-center">
                            <div class="col-6">
                                <p>
                                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-down text-success" viewBox="0 0 16 16">
                                        <path fill-rule="evenodd" d="M8 1a.5.5 0 0 1 .5.5v11.793l3.146-3.147a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 .708-.708L7.5 13.293V1.5A.5.5 0 0 1 8 1z"/>
                                    </svg>
                                   
                                    Revenue
                                </p>
                                <p class=" fw-bold" style="font-size: 20px;">Rp{{ revenue.data }}</p>
                            </div>
                            <div class="col-6">
                                <p>
                                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-up text-danger" viewBox="0 0 16 16">
                                        <path fill-rule="evenodd" d="M8 15a.5.5 0 0 0 .5-.5V2.707l3.146 3.147a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 1 0 .708.708L7.5 2.707V14.5a.5.5 0 0 0 .5.5z"/>
                                    </svg>
                                    Expense
                                </p>
                                <p class=" fw-bold" style="font-size: 20px;">Rp{{ expense.data }}</p>
                            </div>
                        </div>
                        <hr>
                        <div class="text-center my-3">
                            <p>Balance</p>
                            <p class="fw-bold mb-0" style="font-size: 20px;">Rp{{ balance.data }}</p>
                        </div>
                    </div>
                </div>
                <router-link :to="{ name: 'transaction.create'}" class="btn btn-primary btn-sm rounded shadow mb-3 float-right"> 
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-plus-circle me-1" viewBox="0 0 16 16">
                        <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/>
                        <path d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z"/>
                    </svg>
                Add
                </router-link>

                <div class="card rounded shadow">
                    <div class="card-header">
                        Transaction Details
                    </div>
                    <div class="card-body">
                        <div class="row mb-2" v-for="(transaction, index) in transactions.data" :key="index">
                            <div class="col-1 align-items-center">
                                <svg v-if="transaction.type === 'expense'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-up text-danger" viewBox="0 0 16 16">
                                    <path fill-rule="evenodd" d="M8 15a.5.5 0 0 0 .5-.5V2.707l3.146 3.147a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 1 0 .708.708L7.5 2.707V14.5a.5.5 0 0 0 .5.5z"/>
                                </svg>
                                <svg v-else xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-down text-success" viewBox="0 0 16 16">
                                    <path fill-rule="evenodd" d="M8 1a.5.5 0 0 1 .5.5v11.793l3.146-3.147a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 .708-.708L7.5 13.293V1.5A.5.5 0 0 1 8 1z"/>
                                </svg>
                            </div>
                            <div class="col-5">
                                <p class="fw-bold">
                                    {{ transaction.title }}
                                </p>
                                <p style="font-size: 12px;">
                                    {{ transaction.time }}
                                </p>
                            </div>
                            <div class="col-3">
                                <p class="fw-bolder">
                                    {{ transaction.type === "expense" ? `-Rp${transaction.amount}` : `Rp${transaction.amount}` }}
                                </p>
                            </div>
                            <div class="col-3">
                                <div class="btn-group">
                                    <router-link :to="{ name: 'transaction.edit', params:{ id: transaction.id}}" class="btn btn-sm btn-dark">
                                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil-square" viewBox="0 0 16 16">
                                        <path d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"/>
                                        <path fill-rule="evenodd" d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"/>
                                        </svg>
                                    </router-link>
                                    <button class="btn btn-sm btn-danger" 
                                        @click.prevent="destroy(transaction.id, index)"
                                    >
                                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3-fill" viewBox="0 0 16 16">
                                            <path d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"/>
                                            </svg>
                                    </button>
                                </div>
                            </div>
                        </div>
                        <!-- <table class="table">
                            <thead>
                                <tr>
                                    <th>Title</th>
                                    <th>Amount</th>
                                    <th>Type</th>
                                    <th>Action</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr v-for="(transaction, index) in transactions.data" :key="index">
                                    <td>{{ transaction.title }}</td>
                                    <td class="fw-bold">{{ transaction.type === "expense" ? `-Rp${transaction.amount}` : `Rp${transaction.amount}` }}</td>
                                    <td>{{ transaction.time }}</td>
                                    <td>
                                        <div class="btn-group">
                                            <router-link :to="{ name: 'transaction.edit', params:{ id: transaction.id}}" class="btn btn-sm btn-dark">
                                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil-square" viewBox="0 0 16 16">
                                                <path d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"/>
                                                <path fill-rule="evenodd" d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"/>
                                                </svg>
                                            </router-link>
                                            <button class="btn btn-sm btn-danger" 
                                                @click.prevent="destroy(transaction.id, index)"
                                            >
                                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3-fill" viewBox="0 0 16 16">
                                                    <path d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"/>
                                                    </svg>
                                            </button>
                                        </div>
                                    </td>
                                </tr>
                            </tbody>
                        </table> -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import { onMounted, ref } from 'vue';

export default {
    setup() {
        // reactive state
        let transactions = ref([])
        let expense = ref([])
        let revenue = ref([])
        let balance = ref([])

        onMounted(() => {
            // get data from api endpoint
            axios.get('http://localhost:8000/api/transaction')
            .then((result) => {
                transactions.value = result.data
            }).catch((err) => {
                console.log(err.response)
            });
        });

        onMounted(() => {
            // get data from api endpoint
            axios.get('http://localhost:8000/api/transaction/expense')
            .then((result) => {
                expense.value = result.data
            }).catch((err) => {
                console.log(err.response)
            });
        });
        
        onMounted(() => {
            // get data from api endpoint
            axios.get('http://localhost:8000/api/transaction/revenue')
            .then((result) => {
                revenue.value = result.data
            }).catch((err) => {
                console.log(err.response)
            });
        });
        
        onMounted(() => {
            // get data from api endpoint
            axios.get('http://localhost:8000/api/transaction/balance')
            .then((result) => {
                balance.value = result.data
            }).catch((err) => {
                console.log(err.response)
            });
        });
        

        function destroy(id, index) {
             axios.delete(
                `http://localhost:8000/api/transaction/${id}`
            )
            .then(() => {
                transactions.value.data.splice(index, 1)
                location.reload()
            }).catch((err) => {
                console.log(err.response.data);
            });
        }
        
        return {
            transactions,
            revenue,
            expense,
            balance,
            destroy
        }
    }
}
</script>