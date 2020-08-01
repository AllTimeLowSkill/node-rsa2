<template>
    <div>
        <div class="header">
            <h1>Курсовая работа по теме: ЭЦП</h1>
        </div>
        <div class="form_encrypt">
           <form action="" @submit.prevent="rsa_encrypt()">
                <div>
                    <label for="name">Name: </label>
                    <input type="text" v-model="name" name="name" placeholder="Input your name">
                </div>
                <br>
                <div>
                    <label for="pass">Password: </label>
                    <input type="password" v-model="pass" name="pass" placeholder="Input your password">
                </div>
                <hr>
                <div>
                    <button class="button_encrypt" type="submit">Encrypt</button>
                </div>
           </form>
        </div>
        <div class="result_encrypt">
            <div class="header_result">
                <span>Data hash:</span>
            </div>
            <div class="result">
                <span>{{encrypt}}</span>
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'forms',
    data: () => {
        return{
            name: '',
            pass: '',
            encrypt: ''
        }
    },
    methods:{
        rsa_encrypt: function() {
            const NodeRSA = require('node-rsa');
            const key = new NodeRSA({b: 512});

            let text = this.name + ' ' + this.pass;
            this.encrypt = key.encrypt(text, 'base64');
            console.log('encrypted: ', this.encrypt);

            console.log(this.name + ' ' + this.pass);

            return this.encrypt
           
        }
    }
}
</script>

<style lang="scss" scoped>
    .form_encrypt{
        padding-top: 20px;
        padding-bottom: 20px;
        border: 2px solid black;
        margin-bottom: 10px;

        .button_encrypt{
            border: none;
            padding: 10px 15px;
            color: white;
            background-color: blue;

        }

        .button_encrypt:hover{
            color: black;
            background-color: #fff;
            border: 1px solid black;
            padding: 9px 14px;
        }

    }
    .result_encrypt{
        display: flex;
        align-items: center;
        
        border: 2px solid black;

        .header_result{
            flex: 0 1 30%;
            background-color:black;
            color: white;
            font-size: 25px;
            font-weight: 800;
            padding-top: 20px;
            padding-bottom: 20px;
        }

        .result{
            padding-left: 30px;
        }
    }

    .header{
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: blue;
        color: whitesmoke;
        padding-top: 20px;
        padding-bottom: 20px;
    }
</style>


