<template>
  <div class="container">
    <header>
      <h1>The <strong>Anime</strong> Api</h1>
      <form class="search-form">
        <input 
          type="search"
          class="search-input"
          placeholder="Search for an anime" 
          required>
      </form>
    </header>

    <main>
      <div class="cards">
        <Card />
        <Card />
        <Card />
        <Card />
        <Card />
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
  }
}

main{
  padding: 15px 30px;

  .cards{
    display: flex;
    flex-wrap: wrap;
    margin: 0 -10px;
  }
}
</style>
