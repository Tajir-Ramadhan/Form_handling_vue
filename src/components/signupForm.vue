<template>
    <div>
        <form @submit.prevent="handleSubmit">
            <label for="Email">Email:</label>
            <input type="email" name="Email" required v-model="email">

            <label for="Password">Password:</label>
            <input type="password" name="Password" required v-model="password">
            <div v-if="passwordError" class="error">
                {{ passwordError }}
            </div>

            <label>Role:</label>
            <select v-model="role">
                <option value="developer">Web developer</option>
                <option value="designer">Web designer</option>
            </select>

            <label>Skills:</label>
            <input type="text" v-model="tempSkills" @keyup.alt="addSkills">
            
            <div v-for="skill in skills" :id="skill" class="pill" >
                <span @click="deleteSkill(skill)" >{{ skill }}</span>
            </div>

            <div class="terms">
                <input type="checkbox" v-model="term">
                <label>Accept terms and conditions</label>
            </div>

            <div class="submit">
                <button>Create an Account</button>
            </div>
        </form>

        <p>Email: {{ email }}</p>
        <p>Password: {{ password }}</p>
        <p>Role: {{ role }}</p>
        <p>Terms accepted: {{ term }}</p>
        <p>Skills added: {{ skills }}</p>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                email: '',
                password: '',
                role: '',
                term: false,
                tempSkills: '',
                skills: [],
                passwordError: ''
            }
        },
        methods: {
            addSkills(e) {
                if(e.key === ',' && this.tempSkills) {

                    if(!this.skills.includes(this.tempSkills)) {
                        this.skills.push(this.tempSkills)
                    }
                    

                    this.tempSkills = ''
                }
            },
            deleteSkill(skill) {
                this.skills = this.skills.filter( (item) => {
                    return item !== skill
                })
            },
            handleSubmit() {
                //validate password
                this.passwordError = this.password.length > 5 ? '' : 'The password length must be atleast 6 char long!'

                if(!this.passwordError){
                    console.log('email: ',this.email)
                    console.log('Password: ',this.password)
                    console.log('role: ',this.role)
                    console.log('skills: ',this.skills)
                    console.log('Terms Accepted: ',this.term)
                }
            }
        }
    }
</script>

<style >
form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
    border-radius: 5px;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.pill{
    margin: 20px 10px 0 0;
    display: inline-block;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}
button{
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
}
.submit{
    text-align: center;
}
.error{
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;

}
</style>