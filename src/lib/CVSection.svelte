<script>
    let {title = '', skills = [], date = '', content = [], location = ''} = $props();
</script>
<div>
    {#if title !== ''}
        <p id="title">{title}  </p>
    {/if}
    {#if location !== ''}
        <p>| {location}  </p>
    {/if}
    {#if date !== ''}
        <p>| {date}</p>
    {/if}
    {#if skills.length > 0}
        <p>|
            {#each skills as skill, index}
                {#if index === 0}
                    <li class="skills"> {skill}</li>
                {:else}
                    <li class="skills">, {skill}</li>
                {/if}
            {/each}
        </p>
    {/if}

    <ul>
        {#each content as c}
            <li>{c}</li>
        {/each}
    </ul>
</div>


<style>
    p, .skills {
        display: inline;
    }
    
    ul {
        list-style-type: disc;
        margin-left: 15px;
    }
#title{
    font-weight: bold;
}
</style>