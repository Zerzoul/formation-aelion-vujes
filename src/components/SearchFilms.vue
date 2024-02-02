<template>
    <div>
        <form>
            <label for="search">Rechercher :</label>
            <input id="search" type="text" v-model="search">
        </form>

        <div>
            <p>
                <span>{{ moviesFind }} </span> : film(s) trouvé
            </p>
        </div>
        <ul class="films">
            <li v-for="(item, index) in searchFilms" :key="index" class="film card">
              <img :src="item.poster" class="poster"/>
              <p class="title">
                {{ item.title }}
                <span class="rating">{{ display(item.metascore)}} </span>
              </p>
              <dl>
                <dt>Release date</dt><dd>{{item.released}}</dd>
                <dt>Director</dt><dd>{{ item.director }}</dd>
                <dt>Actors</dt><dd>{{ item.actors }}</dd>
                </dl>
                <p class="plot">
                  {{ item.plot }}
                </p>
            </li>
          </ul>
    </div>
</template>

<script>

export default ({
    name: 'SearchFilms',
    data(){
        return {
            search: "",
            searchFilms: [],
            moviesFind: 0
        }
    },

    watch: {
        search() {
            this.searchFilmsSelection
        }
    },

    computed:{
        searchFilmsSelection() {
            this.searchFilms = this.$store.getters.getFilms(this.search)
            this.moviesFind = this.searchFilms.length
        }
    },

    methods:{
        display(rating) {
            let value = ''
            if(parseFloat(rating) < 25) {
                value = '★'
            }else if(parseFloat(rating) < 50) {
                value = '★★'
            }else if(parseFloat(rating) < 75) {
                value = '★★★'
            }else if(parseFloat(rating) < 100) {
                value = '★★★★'
            }else if(parseFloat(rating) === 100) {
                value = '★★★★★'
            }
            return value
        }
    }
})
</script>
