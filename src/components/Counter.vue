<template>
    <h2>  {{ title }} </h2>
    <button v-on:click="incrementar()">+1</button>
    <button @click="decrementar()">-1</button>
    <p> {{ counter }} * {{ counter }} = {{ getMultiply() }} </p>
    <p> {{ counter }} * {{ counter }} = {{ getMultiplyCache }} </p>
</template>

<script>
export default {
    //props: ['title'],
    props: {
        'start': {
            type: Number,
            required: true,
            default: 10,
            validator(val) {
                return val > 100
            }
        },
        'title': String
    },
    data(){
        return {
            counter: this.start
        }
    },
    methods: {
        getMultiply() {
            return this.counter * this.counter;
        },
        incrementar() {
            this.counter++;
        },  
        decrementar() {
            this.counter--;
        }
    },
    computed: {
        // Vue guarda estos metodos en cache
        getMultiplyCache() {
            return this.counter * this.counter;
        }
    }
}
</script>

<style>

button {
    margin: 0 5px;
    background-color: green;
    color: white;
    border-radius: 5px ;
}

button:hover {
    background-color: greenyellow;
}

</style>