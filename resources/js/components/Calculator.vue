<template>

        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header text-center fa-2x">Calculator</div>
                </div>
                <div class="card-body">
                    <div class="calculator">
                        <div class="display">{{ current || '0' }}</div>
                        <div @click="clear" class="btn">C</div>
                        <div @click="sign" class="btn">+/-</div>
                        <div @click="percent" class="btn">%</div>
                        <div class="operator">/</div>
                        <div @click="append('7')" class="btn">7</div>
                        <div @click="append('8')" class="btn">8</div>
                        <div @click="append('9')" class="btn">9</div>
                        <div class="operator">x</div>
                        <div @click="append('4')" class="btn">4</div>
                        <div @click="append('5')" class="btn">5</div>
                        <div @click="append('6')" class="btn">6</div>
                        <div class="operator">-</div>
                        <div @click="append('1')" class="btn">1</div>
                        <div @click="append('2')" class="btn">2</div>
                        <div @click="append('3')" class="btn">3</div>
                        <div class="operator">+</div>
                        <div @click="append('0')" class="zero">0</div>
                        <div @click="dot" class="btn">.</div>
                        <div class="operator">=</div>
                    </div>
                </div>
            </div>
        </div>
    
</template>

<script scoped>
    export default {
        data() {
            return {
                current: '',
            }
        },

        methods: {
            clear() {
                this.current = '';
            },
            sign() {
                this.current = this.current.charAt(0) === '-' ?
                    this.current.slice(1) : `-${this.current}`;
            },
            percent() {
                this.current = `${parseFloat(this.current) / 100}`
            },
            append(number) {
                this.current = `${this.current}${number}` 
            },
            dot() {
                if(this.current.indexOf('.') === -1) {
                    this.append('.');
                }
            }
        },

        mounted() {
            console.log('Component mounted.')
        }
    }
</script>

<style scoped>
    .calculator {
        font-size: 40px;
        display:grid;
        grid-template-columns: repeat(4, 1fr);
        grid-auto-rows: mimax(50px, auto);
        border: 1px solid #333;
    }

    .display{
        background-color: black;
        color: white;
        grid-column: 1 / 5;
        border: 1px solid #333;
        text-align: center;
    }

    .zero{
        grid-column: 1 / 3;
        border: 1px solid #333;
        text-align: center;
    }

    .btn{
        font-size: 30px;
        background-color: #eee;
        border: 1px solid #333;
    }

    .operator{
        text-align: center;
        font-size: 30px;
        background-color: orange;
        border: 1px solid #333;
    }
</style>