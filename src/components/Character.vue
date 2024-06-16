<template>
 <div>
   <h3> MarvelZilla</h3>
   <!--p>{{ this.$route.params.id }}</p-->

   <ul>
     <li v-for="char in character">
       {{ char.name }}
       {{ char.description }}
     </li>
   </ul>

   <img :src="url" alt="">
 </div>
</template>

<script>
import { public_key, private_key, full_hash} from "@/marvel";
import axios from "axios";

export default {
  name: "Character",

  data(){
    return{
      character: [],
      url: '',
      size: 'standard_large.jpg',


    }
  },
  mounted(){
    this.getCharacter()
  },
  methods: {

    getCharacter: function(){

      var characterID = this.$route.params.id

      axios
          .get(`https://gateway.marvel.com:443/v1/public/characters/${characterID}?ts=1&apikey=b3234bbc92bd4663f4a3f556cf61ee81&hash=8e397656b868790f6ad070557ba095f3`)
          .then((result) => {

              console.log(result)

              result.data.data.results.forEach((item) => {

                this.character.push(item)

                this.url = `${item.thumbnail.path}/${this.size}`

                console.log(this.url)
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