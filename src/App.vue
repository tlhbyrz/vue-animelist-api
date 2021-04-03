<template>
  <div class="container">
    <header>
      <h1>The <strong>Anime</strong> Api</h1>
      <form class="search-form" @submit.prevent="getAnimes">
        <input 
          type="search"
          v-model="text"
          class="search-input"
          placeholder="Search for an anime" 
          required>
      </form>
    </header>

    <main>
      <div class="cards" v-if="animeList.length > 0">
        <Card v-for="anime in animeList" :key="anime.mal_id" :anime="anime" />
      </div>
      <div class="no-anime" v-else>
        <h3>No anime to show. Please search an anime!</h3>
      </div>
    </main>
  </div>
</template>

<script>
import Card from "./components/Card"

export default {
  name: 'App',
  components: {
    Card
  },
  data(){
    return{
      text: "",
      animeList: []
    }
  },
  methods: {
    async getAnimes(){
      const res = await fetch(`https://api.jikan.moe/v3/search/anime?q=${this.text}`)
      const { results } = await res.json();
      this.animeList = results;
      this.text = "";
      console.log(results);
      console.log(this.text);
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Livvic:wght@400;500;600;700;900&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  line-height: 1.5;
  font-family: 'Livvic', sans-serif;
}

.container{
  width: 100%;
  max-width: 660px;
  margin: 0 auto;
}

header{
  margin: 50px 0 50px 0;

  h1{
    color: #888;
    text-align: center;
    font-size: 40px;
    text-transform: uppercase;

    strong{
      color: #313131;
    }
  }

  @media screen and (max-width: 500px) {
      h1{
        font-size: 30px;
      }        
  }

  .search-form{
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 0 30px;
    margin-top: 30px;

    .search-input{
      display: block;
      width: 100%;
      max-width: 600px;
      padding: 15px;
      border-radius: 8px;
      font-size: 20px;
      font-weight: 600;
      box-shadow: 0px 4px 8px rgba($color: #000000, $alpha: .15);
      border: none;
      outline: none;
      appearance: none;
      background: #FAFAFA;

      &::placeholder{
        color: #AAA;
      }

      &:focus, &:valid{
        background: #313131;
        color: #fff;
      }
    }

    @media screen and (max-width: 500px) {
      .search-input{
        font-size: 15px;
      }        
    }
  }
}

main{
  padding: 15px 30px;

  .cards{
    display: flex;
    flex-wrap: wrap;
    margin: 0 -10px;
  }

  h3{
    text-align: center;
  } 
}
</style>
