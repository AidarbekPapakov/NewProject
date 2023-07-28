<script>

import { Deta } from 'deta'

  const deta = Deta('d0g4ew7kybk_rBkZah8PE2fo531yPkzg4aWrSq5y2J8D');
  const myNewName = deta.Base('MyNewName');



function addToDataBase(){
  let value = {
    key: key,
    name: userName,
    review: userReview,
    rating: userRating,
 };
  showUserReview=true;
  leaveReview=false;
  let result = myNewName.put(value);
}

  let restaurants = [
      {authour: "John", name: "Take It Cheesy", review: "This place doesn`t really feel the way you might think of it at first, but as soon as you`re served with your order you`ll be surpised. The place is amazing only by it food, let alone professional and polite stuff, and the prices are not expensive at all. Recommend it and I`ll go there one more time", rating: 9.4}, 
      {authour: "Richard", name: "Wingmans Pub", review: "The food is decent, prices are really cheap, and I would say that this place is one of the most rewarding in this city!", rating: 8.6}, 
      {authour: "Beth", name: "Lord of the Fries", review: "My husband and i decided to have a lunch somewhere while we`re outside and we found this place (just fyi, my husband is very picky), I was surprised by the quality of the food and my husband was too. Moreover, the waiters were so cute and had great sense of humor!", rating: 9.8}
  ]
  let safeDistricts = ["Long Island","Capital District","Finger Lakes"]
  let unsafeDistricts = ["Southeren Tier","Hudson Valley","CatSkills"]
  let sightseeings = [
    {name: "The Tower", image: "https://www.planetware.com/photos-large/ENG/england-london-tower-of-london-from-water.jpg", description: "This magnificent tower was built under Ludwig 8, in 1736. It was his gift to people as he said at that time. Nevertheless, 'people' that he meant were not allowed to be on the streets this tower stood. Suprisingly, to this day, it stands intact, retaining its original appearance"},
    {name: "The Bridge", image: "https://cdn.londonandpartners.com/visit/london-organisations/thames-bridges-various/86837-640x360-millennium-bridge-640.jpg", description: "The Great Bridge was built back in the 19th century in honor of the arrival of immigrants from other countries. In addition to its menstrual appearance, this bridge carries over at least 50,000 people every day!"},
    {name: "The Elephant", image: "https://cloudfront-us-east-1.images.arcpublishing.com/pmn/QOPOXXDQP5CAXPNZHCF4XSOIBE.jpg", description: "This elephant is a great asset of this city. Many people do not understand the meaning of this attraction, but if you turn to religious legends, it will immediately become clear how majestic an elephant is in the culture of this country"}
  ]

 let randomNumber = Math.floor(Math.random()*10000);
  let key = randomNumber.toString();
  let userName;
  let userReview;
  let userRating=0;
  let leaveReview = false;
  let showUserReview = false;
  let countForReview = 0;

  let publicTransportImage = "https://upload.wikimedia.org/wikipedia/commons/8/87/Istanbul_Rapid_Transit_Map_with_Metrobüs_%28schematic%29.png";
  let phrases = ["Nihao - Hello", "Bana yardim et - Help me", "Eu não falo a sua língua - I do not speak your language"]
  let weatherForecast = "https://gray-kptv-prod.cdn.arcpublishing.com/resizer/av0_485k8oSIluNroN5F9yny_fU=/800x450/smart/filters:quality(70)/cloudfront-us-east-1.images.arcpublishing.com/gray/6UOSW7TODFD7JHR7PBPHGUYTDI.png";
  let forbiddenActions = [
    {name: "Harassing", detail: "Always treat people with respect because YOU are in their country. When you address someone, do it politely"},
    {name: "Swearing", detail: "You have to respect citizens of other countries. It means you better not swear loudly outside as many people do not like it and there are kids outside as well"},
    {name: "Screaming", detail: "Screaming is considered to be one of the signs of disrespect because you disturb people and their lesuire. When you address someone do it adequate tone, not too loud, but not too silently as well"}
  ]

  let nameRestaurant;
  let nameSightseeing;
  let nameHarassment;
  let showReview = false;
  export let data;

  $: indexOfRestaurants = restaurants.findIndex((item) => item.name == nameRestaurant);
  $: indexOfSightseeings = sightseeings.findIndex((item) => item.name == nameSightseeing);
  $: indexOfActions = forbiddenActions.findIndex((item) => item.name == nameHarassment);
</script>
<nav>
  <a href="/">Home</a>
  <br>
  <a href="/toOptions/one">Back</a>
</nav>


<h1>Here you`ll find everything you should know about "{data.name}"</h1>

{#if data.name=="Best places to eat"}
    {#each restaurants as restaurant}
      <button class='show' on:click={()=>{
        showReview=true
        nameRestaurant=restaurant.name
        userName=undefined
        userReview=undefined
        userRating=undefined
        countForReview=0
        leaveReview=false
        }}>
          {restaurant.name}
      </button>
          <br><br>
    {/each}

    {#if showReview==true && indexOfRestaurants!=-1}
      <button class="hide" on:click={()=>{showReview=false}}>Hide</button>
      
       <p class="authour">{restaurants[indexOfRestaurants].authour}</p>
          <p>
              {restaurants[indexOfRestaurants].review}
                  <br>
              {restaurants[indexOfRestaurants].rating}☆
                  <br><br>
          </p> 
{#if showUserReview==true && userName!=undefined}
        <p class="authour">{userName}</p>
          <p>
            {userReview}
              <br>
            {userRating}☆
              <br><br>
          </p>
          {/if}

          <br><br>

      
          <button class="makeReview" on:click={
          ()=>{
            leaveReview=true 
            countForReview++
          }
          }>Leave Your Review</button>
          {#if countForReview>=2}
          
            <p class="reviewRule">You have already left your review! You cannot leave more than one review!</p>
          
          {/if}
          {#if leaveReview==true && countForReview!=2}
            <p>Your name:</p>

            <input class="userName" bind:value={userName}>

            <p>Your review:</p>

            <input type="text" class="userReview" bind:value={userReview}>

            <p>Your rating:</p>
              {#if userRating!=undefined}
                <p>{userRating}</p>
              {/if}
            <input type="range" min=0.0 max=10.0 step="0.1" class="userRating" bind:value={userRating}>

              
              

            <button class="submit" on:click={addToDataBase}>Submit</button>  
          {/if}
    {/if}

  {:else if data.name=="Safe&Unsafe districts of the city"}
   <div class="safeDistricts">
      <h2>The Safest Districts are:</h2>  
  </div> 

    <p class="warning">These are with the lowest crime rates, but awlays keep in mind that everything can happen</p>

  <br>

    {#each safeDistricts as safeDistrict}
      <p class="district">{safeDistrict}</p>
      <br>
    {/each}

   
    <br><br><br>
  
    <div class="safeDistricts" >
      <h2>The Most Dangerous Districts are:</h2>  
    </div>  
    
    <p class="warning">Be extremely careful about these ones, you might get robbed, injured, and even killed</p> 
  
    <br>
  

        {#each unsafeDistricts as unsafeDistrict}
          <p class="district">{unsafeDistrict}</p>
          <br>
        {/each}

  {:else if data.name=="Sightseeings"}
    
    {#each sightseeings as sightseeing}
    <button class="show" on:click={()=>{nameSightseeing=sightseeing.name}} on:click={()=>{showReview=true}}>
      {sightseeing.name}
    </button> 
    
        <br><br>
    
    {/each}

      {#if showReview==true && indexOfSightseeings!=-1}
        <br><br><br>
      <div>
        <img src={sightseeings[indexOfSightseeings].image} alt={sightseeings[indexOfSightseeings].name}>
          <br>
        <p class="name">
          {sightseeings[indexOfSightseeings].name}
        </p>
        
        <p class="description">{sightseeings[indexOfSightseeings].description}</p>
      </div>
        



      {/if}


  {:else if data.name=="The map of public transport"}    
      <img class="publicTransport" src={publicTransportImage} alt="Public Transport">
      <p class="mapSubway">This is The Map of the subway transport!</p>

  {:else if data.name=="Basic phrases you have to know"}
    {#each phrases as phrase}
    <p class="phrase">{phrase}</p>
    <br>
    {/each} 


  {:else if data.name=="Weather forecast"}

    <h3>
      Weather Forecast for the next week!
    </h3>
      <img class="weather" src={weatherForecast} alt="Weather Forecast">
      
  {:else}

    {#each forbiddenActions as forbiddenAction}
      <button class="action" on:click={()=>{nameHarassment=forbiddenAction.name}} on:click={()=>{showReview=true}}>
        {forbiddenAction.name}
      </button>
      <br><br><br>
    {/each}

    {#if showReview==true}
    <br><br><br>
    <p class="details">{forbiddenActions[indexOfActions].detail}</p>
    {/if}
  
  

{/if}

<style>
.reviewRule{
   border: 1px solid snow;
   border-radius: 20px;
   padding: 20px 45px;
   width: 700px;
   text-align: center;
  }
  .submit{
    position: relative;
    top: 200px;
    left: 465px;
    padding: 5px 15px;
    border: 1px solid snow;
    border-radius: 5px;
    background-color: rgb(46,46,52.5);
    color: snow;
    font-size: 15px;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    opacity: 70%;
  }
  .submit:hover{
    opacity: 100%;
  }
  .submit:active{
    transform: translateY(1px);
  }
  .userName{
    font-size: 16px;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    position: relative;
    top: 210px;
    left: 80px;
    border: 1px solid beige;
    border-radius: 10px;
    padding: 3px 10px;
    background-color: rgb(46,46,52.5);
    color: snow;
  }
  .userReview{
    font-size: 16px;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    position: relative;
    top: 210px;
    left: 80px;
    border: 1px solid beige;
    border-radius: 10px;
    width: 600px;
    height: 100px;
    padding-top: -30px;
    background-color: rgb(46,46,52.5);
    color: snow;
  }
  .userRating{
    position: relative;
    top: 210px;
    left: 80px;
    accent-color: darkseagreen;
    height: 3px;
  }
  .makeReview{
    position: relative;
    top: 180px;
    left: 80px;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    font-size: 18px;
    padding: 5px 15px;
    border: 1px solid snow;
    border-radius: 8px;
    background-color: rgb(46,46,52.5);
    color: snow;
    opacity: 65%;
  }
  .makeReview:hover{
    opacity: 100%;
  }
  .makeReview:active{
    transform: translateY(1px);
  }
  .mapSubway{
    position: relative;
    left: 500px;
    border: 1px solid snow;
    border-radius: 10px;
    padding: 5px 15px;
    width: 400px;
    text-align: center;
    
  }
  .details{
    text-align: center;
    border: 1px solid snow;
    border-radius: 15px;
    padding: 10px 15px;
  }
  .action{
    position: relative;
    top: 250px;
    left: 420px;
    border-style: double;
    border: 1px solid snow;
    background-color: rgb(46,46,52.5);
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    font-size: 20px;
    color: snow;
    border-radius: 40px;
    width: 600px;
    padding: 15px 12px;
    text-align: center;
    opacity: 60%;
  }
  .action:hover{
    opacity: 100%;
  }
  .action:active{
    transform: translateY(1px);
  }
  h3{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    padding: 10px 10px;
    color: snow;
    position: relative;
    top: 160px;
    left: 420px;
    font-size: 32px;
    border: 1px solid snow;
    width: 565px;
    border-radius: 5px;
  }
  .weather{
    position: relative;
    top: 200px;
    left: 300px;
    width: 800px;
  }
  .phrase{
    position: relative;
    left: 380px;
    border: 2px solid snow;
    border-radius: 40px;
    width: 600px;
    padding: 15px 12px;
    text-align: center;
    opacity: 60%;
  }
  .phrase:hover{
    opacity: 100%;
  }
  .publicTransport{
    position: relative;
    top: 180px;
    left: 310px;
    width: 800px;
  }
  .safeDistricts{
    height: 80px;
    text-align: center;
    position: relative;
    left: 480px;
  }
  .description{
    position: relative;
    top: -350px;
    left: 550px;
    width: 700px;
  }
  .name{
    position: relative;
    top: 0px;
    left: 190px;
  }
  img{
    border-top-left-radius: 30px;
    border-top-right-radius: 30px;
    width: 500px;
    border: 2px solid snow;
  }
  .publicTransport{
    border-radius: 30px;
  }
  a:link{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    color: snow;
    text-decoration: none;
    opacity: 40%;
  }
  a:visited{
    color: snow;
    opacity: 40%;
  }
  a:hover{
    color: snow;
    opacity: 100%;
  }
  h2{
    color: white;
    text-align: center;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;

  }
  div{
    border: 2px solid snow;
    border-radius: 30px;
    position: relative;
    top: 180px;
    left: 0px;
    width: 500px;
    height: 400px;
  }
  .district {
    color: white;
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    font-size: 24px;
    text-align: center;
  }
  h1{
    padding: 10px 15px;
    font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet', sans-serif;
    font-size: 30px;
    text-align: center;
    color: snow;
    position: absolute;
    top: 80px;
    left: 720px;
    transform: translate(-50%,-50%);
    background-image: linear-gradient(#F4B183, #FFD89C);
    background-size: 100% 3px;
    background-repeat: no-repeat;
    background-position: 100% 0%;
    -webkit-border-radius: 40px;
        border-radius: 20px;
    -moz-border-radius: 20px;
        border-radius: 20px;
    transition: background-size .7s, background-position .5s ease-in-out;
  }
  h1:hover{
    background-size: 100% 100%;
    background-position: 0% 100%;
    transition: background-position .7s, background-size .5s ease-in-out;
    -webkit-text-stroke: 1px rgb(46,46,52,5);
 }
  .authour{
      top: 220px;
      color:darkseagreen;
  }
  p{
      font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
      font-size: 20px;
      color: snow;
      position: relative;
      top: 220px;
      left: 70px;
      width: 1300px;
      margin: 20px 10px;
  }
  .warning{
    left: 320px;
    text-decoration: underline;
  }
  .hide{
      border: none;
      background-color: rgb(46,46,52,5);
      color: snow;
      font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
      font-size: 16px;
      opacity: 70%;
      position: relative;
      top: 220px;
      left: 75px;
      text-decoration: underline;
  }
  .hide:active{
      transform: translateY(1px);
  }
  .show{
      position: relative;
      background-color: rgb(46,46,52,5);
      left: 600px;
      top: 180px;
      border: 2px solid snow;
      border-radius: 30px;
      border-style: double;
      padding: 10px 10px;
      width: 200px;
      color: snow;
      font-size: 20px;
      font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
      text-align: center;
  }
  .show:hover{
      background-color: rgb(60,60,80);
  }
  .show:active{
      transform: translateY(1px);
  }
</style>

