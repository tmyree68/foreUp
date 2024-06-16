<template>
 <div>
   <h3> MarvelZilla </h3>

   <ul>
     <li v-for="character in characters">
       <router-link :to="{name: 'character', params: {id: character.id}}">{{ character.name }}</router-link>

     </li>
   </ul>
 </div>
</template>

<script>
import { public_key, private_key, full_hash} from "@/marvel";
import axios from 'axios'

export default {
  name: "Characters",

  data(){

    return{
      characters: []
    }
  },

  mounted(){

    this.getCharacters()
  },

  methods:{

    getCharacters: function(){

      axios
          .get('https://gateway.marvel.com:443/v1/public/characters?ts=1&apikey=b3234bbc92bd4663f4a3f556cf61ee81&hash=8e397656b868790f6ad070557ba095f3')
          .then((result) => {

            result.data.data.results.forEach((item) => {

              console.log(item)

              this.characters.push(item)
            })
          })
          .catch((error) => {

            console.log(error)
          })
    }
  }
}
</script>

<style scoped>

</style>