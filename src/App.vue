<template>
  <header>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
  </header>
  <!-- navbar -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-success opacity-90">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Navbar</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <router-link class="nav-link active" aria-current="page" to="/">Pilih Surah Atau Juz</router-link>
          <router-link class="nav-link active" aria-current="page" to="/about">Surah Al-fatihah</router-link>
        </div>
      </div>
    </div>
  </nav>
  <!-- penutup navbar -->
  <router-view/>
</template>