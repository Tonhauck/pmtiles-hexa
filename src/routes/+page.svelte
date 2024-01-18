<script>
  import Map from "../components/Map.svelte";
</script>

<div class="title">Density of bars & pubs in Europe</div>
<div class="map-container">
  <Map />
</div>

<style>
  .map-container {
    width: 100%;
    height: 100vh; /* 100% de la hauteur de la vue (écran) */
    min-height: 100%; /* Hauteur minimale pour éviter que le contenu ne dépasse la carte */
  }
  /* Style pour le titre */
  .title {
    position: absolute;
    z-index: 10000;
    top: 10px; /* Position en haut de la carte */
    right: 10px; /* Position à gauche de la carte */
    background-color: rgba(
      255,
      255,
      255,
      0.8
    ); /* Fond semi-transparent blanc pour le contraste */
    padding: 5px 10px; /* Espacement intérieur pour le texte */
    border-radius: 5px; /* Coins arrondis pour le conteneur du titre */
    font-weight: bold; /* Texte en gras */
  }
</style>
