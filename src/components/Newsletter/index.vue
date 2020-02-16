<template>
    <div class="container newsl_container">
        <h2>Join to our newsletter</h2>
        <div class="form">
            <input type="text" v-model="email">
            <button @click="submitHandler">Subscribe</button>
        </div>
        <div class="error_label">
            <div>{{ error }}</div>
        </div>
        <div class="success_label">
            <div>{{ success }}</div>
        </div>
        <div class="small">
            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Omnis voluptatem non nam tenetur molestias explicabo qui consectetur, ipsa nobis eveniet totam aspernatur, dolor harum repudiandae beatae! Libero asperiores numquam quibusdam!
        </div>
    </div>
</template>

<script>

    /*eslint no-unused-vars: "error"*/

    export default {
        data() {
            return {
                email:'',
                error:'',
                success:''
            }
        },
        methods: {
            validate(email){
                let valid = [true, '']

                if (!/\S+@\S+\.\S+/.test(email)) {
                    valid = [false, 'Enter a valid email']
                }

                if (email === '') {
                    valid = [false, 'Its empty']
                }

                return valid
            },
            submitHandler(){
                let valid = this.validate(this.email);
                if (valid[0]) {
                    this.error = '';
                    this.addEmail(this.email)
                } else {
                    this.error = valid[1]
                }
            },
            addEmail(email){
                this.$http.get(`users.json?orderBy=\"email\"&&equalTo=\"${email}\"`)
                .then( response => {
                    if(Object.getOwnPropertyNames(response.data).length === 0){
                        this.$http.post('users.json',{email: this.email})
                        .then(response => {
                            console.log(response)
                            this.success = 'Thank you'
                        })

                    } else {
                        this.success = 'Already on the list'
                    }
                });
                this.clearSuccess()
            },
            clearSuccess(){
                setTimeout(()=>{
                    this.email = '';
                    this.success = '';
                },3000)
            }
        },
    }
</script>