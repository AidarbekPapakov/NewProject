<script>

    let countries = ["Greece", "Italy", "France", "New Zealand", "Portugal", "Japan", "Brazil", "USA" , "Canada", "The Maldives", "Switzerland", "Norway", "Sweden", "Finland" ]
    let cities = [
    {'name': ['Athens', 'Piraeus', 'Corfu Town']},
    {'name': ['Milan', 'Florence', 'Rome']},
    {'name': ['Paris', 'Strasbourg', 'Bordeaux']},
    {'name': ['Auckland','Christchurch','Queenstown']},
    {'name': ['Lisbon','Coimbra','Leiria']},
    {'name': ['Kyoto','Osaka','Tokyo']},
    {'name': ['Rio de Janeiro','Florianopolis','Salvador']},
    {'name': ['New York City','San Francisco','Los Angeles']},
    {'name': ['Vancouver','Quebec City','Montreal']},
    {'name': ['Malé','Maafushi','Hulhumale']},
    {'name': ['Zürich','Geneva','Bern']},
    {'name': ['Oslo','Bergen','Trondheim']},
    {'name': ['Gothenburg','Stockholm','Malmö']},
    {'name': ['Helsinki','Turku','Rovaniemi']}
    ]

    let suggestedIdeas = [];


   

    let chosenCity;
    let chosenCountry = "Greece";
    let id;
    let suggestIdeas = false;
    let suggestedIdea;
    let submit = false;
    let sentSuggestion = false;

    $: index = (countries.indexOf(chosenCountry)); 

    function addIdeas() {
    suggestedIdeas = [...suggestedIdeas, suggestedIdea]		
    }

    function clickMe() {
    document.querySelector("suggestedIdea").classList.toggle("sliding-away");
    }   


</script>

<br><br>

<div class="border">

<br><br><br>

<h1>This is the best tool for travelling you could ever find</h1>
<h3>The main goal of this site is to help you within different aspects of travelling</h3>


<select bind:value={chosenCountry}>
    {#each countries as country}
        <option value={country}>
            {country}
        </option>
    {/each}
</select>

{#if chosenCity!=''}
<select class="cities" bind:value={chosenCity}>
    {#each cities[index].name as city}
        <option value={city}>
            {city}
        </option>
    {/each}
</select>
{/if}

<br><br><br>
<div class="reference">
    <a href="toOptions/one">See the options</a>
</div>


</div>
<details>
    <summary>
        Who are we?
    </summary>
        <p>Hi there, if you have clicked here you may be interested who we are and why we have made this website.
            The anwser is pretty simple, we are a group of people who just enjoy travelling and have decent expeience at it. 
            As we were travelling we have encountered many troubles that might occur with everyone.
            Hence, we made this site
            to help people like you and us to spend our time more pleasant and efficiently! 
        </p>
</details>

<br><br><br>

<button class="suggestion" on:click={()=>{suggestIdeas=!suggestIdeas}}>If you think of any ideas that might be helpful for a trip feel free to suggest them. We will consider everything</button>

{#if suggestIdeas==true}
    <div class="ideas">
       <div class="arrayOfIdeas">
        {#each suggestedIdeas as idea}
            <div class="suggestedIdea">
                {idea}
            </div>
            <br>
        {/each}
        </div>
    </div>    
    <input bind:value={suggestedIdea} placeholder="Your Idea">
    <button class="submit" on:click={addIdeas}>Sumbit</button>
    <button class="send" on:click={()=>{
        suggestIdeas=false
        sentSuggestion=true
        }}>Send</button>
{/if}
    {#if sentSuggestion==true}
        <p class="sentSuggestion">Your message was successfuly sent!</p>
    {/if}



<br><br>


<style>
    details{
        width: 150px;
    }
    .sentSuggestion{
        color: snow;
        font-size: 18px;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    }
    summary{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 16px;
        text-decoration:underline;
        padding: 6px 12px;
        color: rgb(180, 180, 180);
        position: relative;
        top: -520px;
        left: 645px;
        border: none;
        background-color: rgb(46,46,52.5);
        opacity: 60%;
        text-decoration: none; 
    }
    summary:hover{
        opacity: 100%;
    }
    .suggestedIdea{
        border: 1px solid snow;
        border-radius: 20px;
        width: 150px;
        position: relative;
        left: -35px;
        top: 0px;
        padding: 5px 15px;
    }   
    .arrayOfIdeas{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        position: relative;
        top: -40px;
        left: 670px;
        color: white;
        opacity: 60%;
    }
    .ideas{
        position: relative;
        top: -500px;
    }
    .submit{
        position: relative;
        top: -520px;
        left: 645px;
        border: 1px solid snow;
        border-radius: 20px;
        padding: 5px 15px;
        opacity: 65%;
        background-color: rgb(80, 80, 95);
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: snow;
    }
    .submit:hover{
        opacity: 100%;
    }
    .submit:active{
        transform: translateY(1px);
    }
    .send{
        position: relative;
        top: -480px;
        left: 430px;
        border: 1px solid snow;
        border-radius: 20px;
        padding: 5px 15px;
        opacity: 65%;
        background-color: rgb(80, 80, 95);
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: snow;
    }
    .send:hover{
        opacity: 100%;
    }
    .send:active{
        transform: translateY(1px);
    }
    input{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        background-color: rgb(120, 120, 150);
        border: 1px solid snow;
        border-radius: 20px;
        padding: 5px 15px;
        position: relative;
        top: -520px;
        left: 635px;
        color: snow;
        opacity: 70%;;
    }
    .cities{
        position: relative;
        top: -380px;
        
    }
    p{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 17px;
        color: snow;
        text-align: center;
        opacity: 60%;
        width: 700px;
        position: relative;
        left: 370px;
        top: -500px;
        line-height: 35px;
    }
    .suggestion{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 16px;
        text-decoration:underline;
        padding: 6px 12px;
        color: rgb(180, 180, 180);
        position: relative;
        top: -550px;
        left: 320px;
        border: none;
        background-color: rgb(46,46,52.5);
        opacity: 60%;
        text-decoration: none;
    }
    .suggestion:hover{
        opacity: 100%;
    }
    .suggestion:active{
        transform: translateY(1px);
    }
    .reference{
        position: relative;
        top: -600px;
        left: -30px;
        opacity: 60%;
    }
    .reference:hover{
        opacity: 100%;
    }
    .border{
        border: 5px solid snow;
        border-radius: 20px;
        border-style: double;
    }
    a{
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: snow
    }
    :global(body) {
		background-color: rgb(46,46,52);
	}
    .reference{
        margin-left: 690px;
    }
    select{
    margin: 200px 660px;
    color:black;
    }

    h1 {
    padding: 10px 10px;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet', sans-serif;
    font-size: 30px;
    text-align: center;
    color: snow;
    position: absolute;
    top: 140px;
    left: 720px;
    /* background-image: linear-gradient(190deg, cyan, pink); */
    transform: translate(-50%,-50%);
    background-image: linear-gradient(rgb(123, 226, 103), rgb(50, 216, 225));
    background-size: 100% 3px;
    background-repeat: no-repeat;
    background-position: 100% 0%;
    -webkit-border-radius: 20px;
        border-radius: 20px;
    -moz-border-radius: 20px;
        border-radius: 20px;
    transition: background-size .7s, background-position .5s ease-in-out;
    }
    h1:hover{
    background-size: 100% 100%;
    background-position: 0% 100%;
    transition: background-position .7s, background-size .5s ease-in-out;
    -webkit-text-stroke: 0.5px darkmagenta;
    }
    h3 {
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet', sans-serif;
    text-align: center;
    color: snow;
    position: absolute;
    top: 220px;
    left: 720px;
    transform: translate(-50%,-50%);
    background-image: linear-gradient(rgb(123, 226, 103), rgb(50, 216, 225));
    background-size: 100% 2px;
    background-repeat: no-repeat;
    background-position: 100% 0%;
    transition: background-size .7s, background-position .5s ease-in-out;
    -webkit-border-radius: 20px;
        border-radius: 20px;
    -moz-border-radius: 20px;
        border-radius: 20px;
    padding: 10px 10px;
    }
    h3:hover{
    background-size: 100% 100%;
    background-position: 0% 100%;
    transition: background-position .7s, background-size .5s ease-in-out;
    -webkit-text-stroke: 0.5px rgb(210, 126, 17);
    
    }

</style>
