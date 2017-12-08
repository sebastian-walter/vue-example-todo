<template>
    <div>
        <image-test :src="src"></image-test>
        <h1>Todo</h1>
        {{ message }}
        <ul>
            <li v-for="item in todos">
                <input type="checkbox" :id="item.id" v-model="item.checked">
                <label :for="item.id">{{ item.label }}</label>
            </li>
        </ul>
        <input v-model="newItem">
        <button @click="save">Save</button>
    </div>
</template>

<script>
    import ImageTest from './Image.vue';
    import axios from 'axios';

    export default {
        name: 'Todo',
        data() {
            return {
                message: 'Hallo',
                todos: [

                ],
                newItem: '',
                src: '',
            }
        },
        components: {
            ImageTest,
        },
        methods: {
            save() {
                this.todos.push({
                    id: this.todos.length,
                    label: this.newItem,
                    checked: false,
                });
                this.newItem = '';
            }
        },
        mounted() {
            alert('mounted');
            axios.get('https://dog.ceo/api/breeds/image/random')
                .then(response => {
                    this.src = response.data.message;
                })
        }
    }
</script>