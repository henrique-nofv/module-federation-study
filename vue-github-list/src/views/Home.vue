<template>
    <div>
        <input v-model="userInput" type="text" id="fname" name="firstname" placeholder="Ex: henrique-nofv">
        <input @click="findGithubUsers" type="submit" value="Buscar">
        <div v-if="users.length">
            <div v-for="(user,index) in users" :key="index">
                <img :src="user.avatar_url" alt="Avatar" class="avatar">
                <a :href="user.html_url">{{user.login}}</a>
                <hr>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            userInput: '',
            users: []
        }
    },
    methods: {
        async findGithubUsers() {
            try {
                const response = await axios.get('https://api.github.com/search/users',  { params: {
                        q: this.userInput
                    }
                })

                this.users = response.data.items;
            } catch (error) {
                throw new Error('Failed search users!')
            }
        }
    }
}
</script>

<style scoped>
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=submit] {
  width: 100%;
  background-color: #7728ab;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #b34ed4;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

.avatar {
  vertical-align: middle;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  margin-right: 50px;
}
</style>