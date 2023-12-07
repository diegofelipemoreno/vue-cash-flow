<template>
    <div class="movement">
        <div class="content">
            <h4>{{ title }}</h4>
            <p>{{ description }}</p>
        </div>
        <div class="action">
            <img src="@/assets/trash-icon.svg" alt="borrar" @click="$emit('remove', id)" />
            <p :class="{
                'red': isNegative,
                'green': !isNegative
            }"
            >{{currencyValue}}</p>
        </div>
    </div>
</template>

<script>
    /*
        API style
        import {defineEmits} from 'vue'; 
        const emit = defineEmits(['remove']);

        const remove = (e) => {
            emit('remove', this)
        };
    */

    export default {
        props: {
            id: Number,
            title: String,
            description: String,
            amount: Number
        },
        computed: {
            currencyValue() {
                return new Intl.NumberFormat('es-MX', {
                    style: "currency",
                    currency: "MXN"
                }).format(this.amount);
            },
            isNegative() {
                return this.amount < 0;
            }
        }
    }
</script>

<style scoped>
    .movement {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 16px;
    background-color: #e6f9ff;
    border-radius: 8px;
    box-sizing: border-box;
    }

    .movement .content {
    width: 100%;
    }

    .movement .action {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    flex-direction: column;
    }

    h4,
    p {
    margin: 0;
    padding: 0;
    }

    h4 {
    margin-bottom: 8px;
    }

    .movement .action img {
    margin-bottom: 16px;
    }

    .red {
    color: red;
    }

    .green {
    color: green;
    }
</style>