<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

  <div v-for="surahs in surah" :key="surah.id" class="text-center mt-4">
    <h1 >nama surah {{surahs.name_simple}} ( {{surahs.name_arabic}} )</h1>
    <h5>Diturunkan Di Kota {{surahs.revelation_place}}</h5>
    <h5>Arti Surah {{surahs.translated_name['name']}}</h5>
  </div>

  <br>

      <span v-for="a in ayah" :key="ayah.id" class="text-center mt-4">
        <h5 class=" pt-3">{{ a.text_uthmani }} {{a.verse_key}}</h5>
        <br>
      </span>

  <br>

      <h3 class="text-center pt-4 mb-3">Terjemahan surah</h3>
  <div v-for="a in arti" :key="arti.id" class="text-center pt-2">
      <h6>
        {{a.text}}
      </h6>
  </div>

  <br>

  <h4 class="text-center">Kandungan Surah</h4>

  <br>

  <div v-for="infos in info" :key="info.id">
    <p>
      {{infos.short_text}}
    </p>
    <p>
      {{infos.text}}
    </p>
  </div>

</template>

<script>
import axios from "axios";
import { ref } from "vue";
export default {
  data(){
    return{
      ayah:ref([]),
      surah:ref([]),
      arti:ref([]),
      info:ref([])
    }
  },
  mounted() {
    this.getayah()
    this.getsurah()
    this.getarti()
    this.getinfo()
  },
  methods:{
    getayah(){
      axios.get('https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=1')
      .then(res => {
        this.ayah = res.data.verses
        console.log(res.data.verses)
      })
    },
    getsurah(){
      axios.get('https://api.quran.com/api/v4/chapters/1?language=id')
      .then(res => {
        this.surah = res.data
        console.log(res.data)
      })
    },
    getarti(){
      axios.get('https://api.quran.com/api/v4/quran/translations/33?chapter_number=1')
      .then(res => {
        this.arti = res.data.translations
        console.log(res.data.translations)
      })
    },
    getinfo(){
      axios.get('https://api.quran.com/api/v4/chapters/1/info?language=id')
      .then(res => {
        this.info = res.data
        console.log(res.data)
      })
    }
  }
}
</script>