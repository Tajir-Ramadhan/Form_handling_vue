<template>
    <div>
        <form action="">
            <label for="Email">Email:</label>
            <input type="email" name="Email" required v-model="email">

            <label for="Password">Password:</label>
            <input type="password" name="Password" required v-model="password">

            <label>Role:</label>
            <select v-model="role">
                <option value="developer">Web developer</option>
                <option value="designer">Web designer</option>
            </select>

            <div class="terms">
                <input type="checkbox" v-model="term">
                <label>Accept terms and conditions</label>
            </div>

            <div class="terms">
                <input type="checkbox" value="Shaun" v-model="names">
                <label>Shaun</label>
            </div>
            <div class="terms">
                <input type="checkbox" value="Yoshi" v-model="names">
                <label>Yoshi</label>
            </div>
            <div class="terms">
                <input type="checkbox" value="Mario" v-model="names">
                <label>Mario</label>
            </div>
            
        </form>
        <p>Email: {{ email }}</p>
        <p>Password: {{ password }}</p>
        <p>Role: {{ role }}</p>
        <p>Terms accepted: {{ term }}</p>
        <p>Names: {{ names }}</p>
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
                names: []
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
</style>