<template>
    <div class="calculator">
        <div class="display2">
            <small class="final-amount-title">--FINAL PRICE--</small>
            <span class="final-amount">{{ percent() }}</span>
        </div>
        <div class="display">
            <div class="left-box">
                <small class="tax-amount-title">TAX</small>
                <span class="tax-amount">8<span class="percentage">%</span></span>
            </div>
            <div class="right">
                <small class="before-tax">Before Tax</small>
                <span class="input-title">{{ current || '0' }}</span>
            </div>
        </div>

        <div @click="append('7')" class="btn">7</div>
        <div @click="append('8')" class="btn">8</div>
        <div @click="append('9')" class="btn">9</div>
        <div @click="append('4')" class="btn">4</div>
        <div @click="append('5')" class="btn">5</div>
        <div @click="append('6')" class="btn">6</div>
        <div @click="append('1')" class="btn">1</div>
        <div @click="append('2')" class="btn">2</div>
        <div @click="append('3')" class="btn">3</div>
        <div @click="dot" class="btn">.</div>
        <div @click="append('0')" class="btn">0</div>
        <div @click="clear" class="btn">x</div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                previous: null,
                current: '',
                operator: null,
                operatorClicked: false,
            }
        },
        methods: {
            clear() {
                this.current = '';
            },
            percent() {
                let a = `${parseFloat(this.current) * 8 / 100}`;
                if (!isNaN(a)) {
                    return parseFloat(parseFloat(this.current) + parseFloat(a)).toFixed(2);
                } else {
                    return 0;
                }
            },
            append(number) {
                if (this.operatorClicked) {
                    this.current = '';
                    this.operatorClicked = false;
                }
                this.current = `${this.current}${number}`;
            },
            dot() {
                if (this.current.indexOf('.') === -1) {
                    this.append('.');
                }
            },
        }
    }
</script>

<style scoped>
    .calculator {
        margin: 0 auto;
        width: 300px;
        height: 550px;
        font-size: 20px;
        display: grid;
        grid-template-columns: auto auto auto;
        text-align: center;
        transparent: 30%;
    }

    .display2 {
        grid-column: 1 / 4;
        background-color: #7F76F4;
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: 100%;
        padding-bottom: 25px;
    }

    .display {
        grid-column: 1 / 4;
        background: white;
        box-shadow: 0 0 15px #363C4C;
        height: 80%;
        display: flex;
        margin-top: 30px;
        align-items: center;
    }

    .left-box {
        background: linear-gradient(-0.85turn, #6BD966, #77DC70);
        transform: scaleY(1.1);
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 30%;
        height: 95%;
    }

    .before-tax {
        color: #73716F;
        font-size: 14px;
    }

    .input-title {
        font-size: 40px;
        font-weight: 100;
    }

    .tax-amount-title {
        color: white;
        font-size: 7px;
        font-weight: 500;
        text-align: center;
        letter-spacing: 1px;
        width: 60%;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
    }

    .tax-amount {
        color: white;

    }

    .final-amount {
        font-size: 62px;
        font-weight: 200;
    }

    .final-amount-title {
        font-size: 10px;
        margin-top: 15px;
    }

    .right {
        justify-content: center;
        align-items: center;
        margin-left: 30px;
        display: flex;
        flex-direction: column;
    }

    .btn {
        background-color: #363C4C;
        border: 1px solid #393E4D;
        color: white;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
        -webkit-transition: width 2s; /* Safari */
        transition: width 2s;
        transparent: 30%;

    }

    .btn:hover {

        /*box-shadow: 0px 0px 10px;*/
        /*transparent: 30%;*/
        transform: translate(1px, 3px)
        /*position: relative;*/
        /*top: -5px;*/
    }

</style>