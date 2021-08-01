<script>
    export let poll;

    //reactive values
    $: totalVotes=poll.votesA+poll.votesB;
</script>

<div class="poll">
    <h3>{poll.question}</h3>
    <p>totalVotes: {totalVotes}</p>
    <div class="answear">
        <div class="percent percent-a"></div>
        <span>{poll.answearA} ({poll.votesA})</span>
    </div>
    <div class="answear">
        <div class="percent percent-b"></div>
        <span>{poll.answearB} ({poll.votesB})</span>
    </div>
</div>


<style>
    h3{
        margin: 0 auto;
        color: #555;
    }
    p{
        margin-top: 6px;
        font-size: 14px;
        color:#aaa;
        margin-bottom: 30px;
    }
    .answear{
        background: #fafafa;
        cursor: pointer;
        margin: 10px auto;
        position: relative;
    }
    .answear:hover{
        opacity: 0.6;
    }
    span{
        display: inline-block;
        padding: 10px 20px;
    }
</style>