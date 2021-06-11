<template>
    <form>
        <label for="Email">Email:</label>
        <input type="email" required v-model="email"> 

        <label for="Password">Password:</label>
        <input type="password" required v-model="password"> 

        <label>Role:</label>
        <select v-model="role">
            <option name="developer">Web Developer</option>
            <option name="designer">Web Designer</option>
        </select>
        <div class="terms">
            <input type="checkbox" v-model='terms' required>
            <label>Accept terms and conditions</label>
        </div>

        <div class="people">
            <input type="checkbox" value="Shaun" v-model='names'>
            <label for="names">Shaun</label>
            <input type="checkbox" value="Mario" v-model='names'>
            <label for="names">Mario</label>
            <input type="checkbox" value="Sam" v-model='names'>
            <label for="names">Sam</label>
        </div>

        <div class='skills'>
            <label for="">Skills:</label>
            <input type="text" v-model="tempSkill" v-on:keyup="addskill">
            <div v-for="skill in skills">
                <p @click="removeSkill(skill)">{{skill}}</p>
            </div>
        </div>
    </form> 

    <p>Email: {{email}}</p>
    <p>password: {{password}}</p>
    <p>Role: {{role}}</p>
    <p>Terms Accepted:{{terms}}</p>
    <p>Names:{{names}}</p>

</template>
<script>
export default {
    data(){
        return{
            email: '',
            password:'',
            role:'',
            terms: false,
            names:[],
            tempSkill: '',
            skills:[]
        }
    },
    methods:{
        // e is inbuilt click event
        addskill(e){
            // check if tempSkill has some value in it
            if(e.key === ',' && this.tempSkill){
                
                // removes the comma that appears with text
                this.tempSkill = this.tempSkill.replace(/,/g,"")
                // prevents duplication of data in array
                //this.tempSkill.replace(',','')
                if (this.skills.includes(this.tempSkill) == false){
                    this.skills.push(this.tempSkill)    
                }
                // resetting the input in array
                this.tempSkill = ''
            }
        },
        removeSkill(skill){
            // es6 way to remove an item from list
            this.skills = this.skills.filter(item => item !== skill)
            //---- pop only removes the latest item in the queue
            // this.skills.pop() 
            console.log(this.skills);
        }
    }
}
</script>
<style>

</style>