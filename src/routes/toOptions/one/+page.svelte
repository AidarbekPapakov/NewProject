<script>

    let arrs = [
      {name: "Sightseeings", id: 1, img: "https://res.klook.com/images/fl_lossy.progressive,q_65/c_fill,w_1280,h_853/w_79,x_14,y_14,g_south_west,l_Klook_water_br_trans_yhcmh3/activities/uy2jyc8oy1lcyanhqwea/LondonCitySightseeingBusPass.webp"}, 
      {name: "Best places to eat", id: 2, img: "https://images.adsttc.com/media/images/5e4c/1025/6ee6/7e0b/9d00/0877/large_jpg/feature_-_Main_hall_1.jpg?1582043123"}, 
      {name: "Safe&Unsafe districts of the city", id: 3, img:"https://gsc-public-1.s3.ap-southeast-2.amazonaws.com/s3fs-public/central_cover.jpg?VersionId=B8BRdgO7w3f7FJmlA6kvle5_xbLArnTd"}, 
      {name: "The map of public transport", id: 4, img:"https://www.mapsland.com/maps/europe/austria/vienna/public-transportation-map-of-vienna-city.jpg"}, 
      {name: "Basic phrases you have to know", id: 5, img:"https://www.oneworld365.org/img/000/45/45678.png"}, 
      {name: "Weather forecast", id: 6, img:"https://patch.com/img/cdn20/users/23195148/20190912/102748/styles/patch_image/public/rain-sun___12101512519.jpg"},
      {name: "The actions you should not do in the city&country", id: 7, img:"https://mlhmvq6amqed.i.optimole.com/cb:WANK~27a14/w:auto/h:auto/q:mauto/f:avif/https://hackspirit.com/wp-content/uploads/2022/01/pexels-keira-burton-6147403.jpg"}
    ]


</script>
<nav>
  <a href="/">Home</a>
</nav>

<br><br>

<div class="cap">
  <h1>Here you can find many guides that will make your trip more pleasant</h1>
  <br>
</div>

<br><br>

<div class="main">
  {#each arrs as arr, i}
    <div class="block">
      <img src={arr.img} alt=img>
      <p><a href="/toOptions/{arr.name}">{arr.name}</a></p> 
    </div>
    {#if (i + 1) % 3 === 0}
      <br>
    {/if}
  {/each}
</div>

<style>
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
  .cap{
    border: 2px solid snow;
    border-radius: 50px;
    padding: 10px 30px;

  }
  a{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    color: snow;
  }
  img{
    /* border-radius: 50px; */
    border-top-left-radius: 50px;
    border-top-right-radius: 50px;
    object-fit: fill;
    width: 385px;
    margin-left: -20px;
    margin-top: -20px;
  }
  .main {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.block {
  border: 2px solid rgb(200, 200, 200);
  border-radius: 50px;
  padding: 20px; 
  margin: 20px; 
  width: calc(33.33% - 80px); 
  box-sizing: border-box; 
  text-align: center;
}

h1 {
  text-align: center;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet', sans-serif;
  color: rgb(46, 46, 52,5);
  font-size: 55px;
-webkit-text-stroke: 0.5px rgb(161, 212, 33);
}

p {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet', sans-serif;
  font-size: 20px;
  color: snow;
}
p:hover{
  transform: translateY(1.5px);
}
</style>