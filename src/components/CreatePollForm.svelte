<script>
    import PollStore from '../Stores/PollStore.js';
import {createEventDispatcher} from 'svelte';
import Button from './../shared/Button.svelte';
let fields={question:" ",answearA:" ",answearB:"  "};
let errors={question:" ",answearA:" ",answearB:"  "};
let valid=false;
let dispatch=createEventDispatcher();


const submitHandler=()=>{
    valid=true;
    if(fields.question.trim().length<5){
        valid=false;
        errors.question='Question must be 5 characters long';
    }else{
        errors.question='';
    }


    if(fields.answearA.trim().length<1){
        valid=false;
        errors.answearA='Answear A cant be empty';
    }else{
        errors.answearA='';
    }


    if(fields.answearB.trim().length<1){
        valid=false;
        errors.answearB='Answear B cant be empty';
    }else{
        errors.answearB='';
    }


    //add new poll
    if(valid){
        let poll={...fields,votesA:0,votesB:0,id:Math.random()}
        //save new poll to store 
        PollStore.update(currentPolls=>{
            return [poll,...currentPolls];
        });
        console.log('valid',fields)
    }

}
</script>



<form on:submit|preventDefault={submitHandler}>
    <div class="form-field">
        <label for="question">Poll Question:</label>
        <input type="text" id="question" bind:value={fields.question}>
        <div class="error">{errors.question}</div>
    </div>
    <div class="form-field">
        <label for="answear-a">Answear A: </label>
        <input type="text" id="answear-a" bind:value={fields.answearA}>
        <div class="error">{errors.answearA}</div>

    </div>
    <div class="form-field">
        <label for="answear-b">Answear B:</label>
        <input type="text" id="answear-b" bind:value={fields.answearB}>
        <div class="error">{errors.answearB}</div>

    </div>
    <Button type="secondary" flat={true} >Add poll</Button>
        
</form>



<style>

form{
    width: 400px;
    margin: 0 auto;
    text-align: center;
}
.form-field{
    margin:18px auto;
}
input{
    width: 100%;
border-radius: 6px;}

label{
    margin:10px auto;
    text-align: left;
}

.error{
    font-weight: bold;
    font-size: 12px;
    color:#d91b42;
}

</style>