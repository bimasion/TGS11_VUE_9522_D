<template>
  <v-card>
        <v-card-text>
            <v-form>
                <v-text-field v-model="form.email" label="Email" name="email" type="text"/>
                <v-text-field v-model="form.password" label="Password" name="password" type="password"/>
            </v-form>
        </v-card-text>
        <v-card-actions>
            <v-spacer />
            <v-btn color="primary" @click="login()">Login</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script>

    export default {
        data () {
            return {
                form: {
                    'email': '',
                    'password': ''
                },

                user: new FormData,
            }
        },

        methods: {
            login() {
                this.user.append('email', this.form.email);
                this.user.append('password', this.form.password);

                var uri = this.$apiUrl + '/user/login';

                this.$http.post(uri, this.user).then(response => {
                    if(response.data.error === false) {
                        this.$router.push('/user/')
                    }
                        
                    else
                        alert('salah boy')
                }).catch(error => {
                    alert('Error')
                })
                
            }
        }
    }

</script>