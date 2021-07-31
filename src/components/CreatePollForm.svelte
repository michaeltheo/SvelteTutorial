<script>
let fields={question:" ",answearA:" ",answearB:"  "};
const submitHandler=()=>{
    console.log(fields);
}
</script>



<form on:submit|preventDefault={submitHandler}>
    <div class="form-field">
        <label for="question">Poll Question:</label>
        <input type="text" id="question" bind:value={fields.question}>
    </div>
    <div class="form-field">
        <label for="answear-a">Answear A: </label>
        <input type="text" id="answear-a" bind:value={fields.answearA}>
    </div>
    <div class="form-field">
        <label for="answear-b">Answear B:</label>
        <input type="text" id="answear-b" bind:value={fields.answearB}>
    </div>
    <button>Add Poll</button>
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

</style>