<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0, maximum-scale=1"
    />
    <title>Anime Finder</title>
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: Arial, sans-serif;
      }

   body {
        background: linear-gradient(to right, #141e30, #243b55);
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
      }
    .container {
        width: 400px;
        background: white;
        padding: 30px;
        border-radius: 15px;
        text-align: center;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
      }
      h1{
   color:white;
   margin-bottom:20px;
}
      .search-container {
        display: flex;
        gap: 10px;
        margin-bottom: 20px;
      }
      input{
   padding:10px;
   width:220px;
   border:none;
   border-radius:5px;
}
      }

input:focus {
        border-color: #ff4757;
      }
      button {
        padding: 12px 18px;
        border: none;
        background: #ff4757;
        color: white;
        border-radius: 5px;
        cursor: pointer;
        transition: 0.3s;
      }


button:hover {
        background: #e84118;
      }
      .anime-box img {
        width: 200px;
        height: 280px;
        object-fit: cover;
        border-radius: 10px;
        margin-bottom: 15px;
      }
      .anime-box h2 {
        margin-bottom: 10px;
        color: #222;
      }
      .anime-box h3 {
        margin-bottom: 10px;
        color: #555;
      }
      .anime-box p {
        color: #666;
      }
    </style>
  </head>
  <body>
    <div class="container">
<h1>Anime Finder</h1>
<div class="search-container">

 <input type="text" id="searchInput" placeholder="Enter anime name">
 <button onclick="searchAnime()">Search</button>
</div>
<div class="anime-box">

<img id="animeImage">
<h2 id="title"></h2>
      <h3 id="rating"></h3>
      <p id="episodes"></p>
    </div>

  </div>
<script>
   async function searchAnime(){

let anime = document.getElementById("searchInput").value;
          let url = `https://api.jikan.moe/v4/anime?q=${anime}`;
          let response = await fetch(url);
          let data = await response.json();
          console.log(data);
          let image = document.getElementById("animeImage");
          image.src = data.data[0].images.jpg.image_url;
          let title = document.getElementById("title");
          title.innerHTML = data.data[0].title;
          let rating = document.getElementById("rating");
          rating.innerHTML = "⭐ Rating: " + data.data[0].score;
          let episodes = document.getElementById("episodes");
          episodes.innerHTML = "Episodes: " + data.data[0].episodes;
      }
</script>
      </body>
