<script>
  import {
    MapLibre,
    LineLayer,
    VectorTileSource,
    FillLayer,
  } from "svelte-maplibre";
</script>

<MapLibre
  style="https://basemaps.cartocdn.com/gl/positron-gl-style/style.json"
  class="map"
  standardControls
  center={[2.35, 48.878781]}
  zoom={5}
  minZoom={8}
>
  <VectorTileSource
    url={"pmtiles://static/BAR_EUROPE_ENTIER_without_Scand.pmtiles"}
  >
    <FillLayer
      paint={{
        "fill-opacity": [
          "interpolate",
          ["linear"],
          ["zoom"], // Utilisation de "zoom" pour l'interpolation en fonction du niveau de zoom
          0,
          1, // Opacité maximale au niveau de zoom 0
          14, // Zoom intermédiaire où vous souhaitez ajuster l'opacité
          0.9, // Opacité minimale au niveau de zoom 14
          18, // Zoom maximum où vous souhaitez ajuster l'opacité
          1, // Opacité minimale au niveau de zoom 18
        ],
        "fill-color": [
          "interpolate",
          ["linear"],
          ["get", "NUMPOINTS"],
          0,
          "rgba(214, 214, 214,0.2)", // Blanc pour NUMPOINT=0
          70,
          "rgba(255, 0, 0,0.7)", // Blanc pour NUMPOINT=0
          149,
          "rgba(127, 10, 10,1)", // Rouge grenade pour NUMPOINT=100 (ajustez cette valeur selon vos besoins)
        ],
      }}
      sourceLayer={"bar_europe"}
    />
  </VectorTileSource>
</MapLibre>

<style>
  :global(.map) {
    height: 100%;
  }
</style>
