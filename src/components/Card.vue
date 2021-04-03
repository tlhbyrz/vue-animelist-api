<template>
  <a :href="anime.url" target="_blank">
    <div class="card">
      <img class="card-img" :src="anime.image_url" alt="Naruto img">
      <h3>{{ anime.title }}</h3>
    </div>
  </a>
  
</template>

<script>
export default {
    name: "Card",
    props: ["anime"]
}
</script>

<style lang="scss" scoped>
a{
    text-decoration: none;
    display: inline-block;
    width: 100%;
    max-width: calc(100% / 3);
    color: #313131;

    .card{
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    cursor: pointer;

    .card-img{
        width: 100%;
        border-radius: 10px;
        transition: .4s;
    }

    h3{
        padding: 5px 10px;
        text-align: center;
    }

    &:hover{
        .card-img{
            transform: scale(1.05);
        }
    }
}

@media screen and (max-width: 500px) {
    .card{
       max-width: calc(100% / 2); 
    }        
}
}


@media screen and (max-width: 370px) {
    .card{
       max-width: calc(100%); 
    }        
}
</style>