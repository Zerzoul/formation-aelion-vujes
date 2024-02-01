<template>
    <div>
        <form>
            <label for="search">Rechercher :</label>
            <input id="search" type="text" v-model="search">
        </form>


        <ul class="films">
            <li v-for="(item, index) in films" :key="index" class="film card">
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
            searchFilms: []
        }
    },

    props: {
        films: Array
    },

    computed:{
        searchFilmsSelection() {
            this.searchFilms.push(this.films)
            return this.searchFilms
        }
    },

    methods:{
        display(rating) {
        let value = ''
        switch(parseFloat(rating)){
            case 0 >= 25:
            value = '★'
            break;
            case 25 >= 50:
            value = '★★'
            break;
            case 50 >= 75:
            value = '★★★'
            break;
            case 75 >= 100:
            value = '★★★★'
            break;
        }
        console.log(value)
        return value
        }
    }
})
</script>
