<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
  <div class="text-center">
    <h1>Pilih Surah Atau Juz</h1>
  </div>

  <br>

  <div class="dropdown text-center">
    <button class="btn btn-success dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
      Pilih Surah
    </button>
    <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
      <li v-for="surah in surahs" :key="surah.id"><router-link class="dropdown-item" to="#">{{surah.name_complex}}</router-link></li>
    </ul>

    <button class="btn btn-success dropdown-toggle" type="button" id="dropdownMenuButton2" data-bs-toggle="dropdown" aria-expanded="false">
      Pilih Juz
    </button>
    <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
      <li v-for="juz in juzs" :key="juz.id"><router-link class="dropdown-item" to="#">{{juz.juz_number}}</router-link></li>
    </ul>

  </div>

</template>

<script>
import {ref} from "vue"
import axios  from "axios";
export default {
  data(){
    return{
    surahs:ref([]),
      juzs:ref([])
    }
  },
  mounted() {
    this.getsurah()
    this.getjuz()
  },
  methods: {
    getsurah(){
      axios.get('https://api.quran.com/api/v4/chapters?language=en')
      .then(res => {
        this.surahs = res.data.chapters
        console.log(res.data.chapters)
      })
    },
    getjuz(){
      axios.get('https://api.quran.com/api/v4/juzs')
      .then(res => {
        this.juzs = res.data.juzs
        console.log(res.data.juzs)
      })
    }
  }
}
</script>