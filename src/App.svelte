<!-- Script JS -->
<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import { onMount } from "svelte";
    let count, index, offset, progress;
    let top = 0.1, threshold = 0.5, bottom = 0.9;
</script>
<main>
    <div class="portada">
        <img src="images/portada.png" alt="Portada" style="width: 100%; height: auto;">
    </div>
    <div class="paises">
        <div class="grafico_paises">
            <iframe title="Mundial 2022" aria-label="Mapa" id="datawrapper-chart-4ppPT" src="https://datawrapper.dwcdn.net/4ppPT/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
        <!--ACLARAR:GALES EN 2022-->
            <p>Gales forma parte del Reino Unido con el puesto numero 30</p>
        </div>
    </div>
    <div class="paises">
        <div class="grafico_paises"></div>
            <iframe title="Mundial 1986" aria-label="Map" id="datawrapper-chart-BWQLZ" src="https://datawrapper.dwcdn.net/BWQLZ/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
        
        <!--ACLARAR: WEST GERMANY/SCOTLAND, NORTH IRELAND EN 1986-->
            <p>Alemania Occidental puesto numero 2, Escocia forma parte del Reino Unido con puesto 19 e Irlanda del norte con puesto 21</p>
        </div>
    <div class="paises">
        <div class="graficos_paises">
            <iframe title="Mundial 1978" aria-label="Map" id="datawrapper-chart-oL8XV" src="https://datawrapper.dwcdn.net/oL8XV/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>

        <!--ACLARAR: WEST GERMANY/SCOTLAND 18986 Y 1978-->
            <p>Alemania Occidental puesto numero 6, Escocia forma parte del Reino Unido con puesto 11</p>
        </div>
    </div> 
</main>



<!-- Estilos CSS -->
<style>

</style>
