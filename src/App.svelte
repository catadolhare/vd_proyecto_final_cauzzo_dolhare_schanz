<!-- Script JS -->
<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import { onMount } from "svelte";
    let count, index, offset, progress;
    let top = 0.1, threshold = 0.5, bottom = 0.9;
    let showInfo = false;

    function toggleInfo() {
        showInfo = !showInfo;
    }
</script>
<main>
    <head>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300..700&display=swap" rel="stylesheet">

        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100..900&display=swap" rel="stylesheet">
    </head>
    <div class="intro">
        <div class="portada">
            <img src="images/portada.png" alt="Portada" style="width: 100%; height: auto;">
        </div>
        <div class="intro1">
            <p>Una comparativa de las tres seleccionas argentinas que se hicieron con el campeonato del mundo</p>
            <p>------------------------------------------------------------------------------------</p>
            <h5>¿Quiénes fueron los protagonistas?</h5>
            <h5>¿Qué los hizo ganar?</h5>
            <h5>¿En qué se diferecian y en qué se asemejan?</h5>
        </div>
        <div class="player">
            <button class="button" on:click={toggleInfo}>
                Tocá para musicalizar
            </button>
            {#if showInfo}
                <div class="alert-overlay">
                    <div class="alert-box">
                        <button class="close-button" on:click={toggleInfo}></button>
                        <h2>Alerta</h2>
                        <p>Esta es una alerta con información importante.</p>
                        <button class="button" on:click={toggleInfo}>Cerrar</button>
                    </div>
                </div>
            {/if}
        </div>
    </div>
    <div class="fondo_intro2">
        <div class="intro2">
            <img src="images/copa.png" alt="Copa del mundo" style='height: 450px'>
            <div class="texto">
                <h2 style='margin:20px 0;'>Más que una competencia</h2>
                <p style='margin:0 10px;'>La Copa Mundial de la FIFA se ha convertido en el torneo deportivo más aclamado del mundo. Durante años ha sabido atrapar a conocedores y a aficionados, ofreciendo una mezcla única de emoción, pasión y talento. Desde su inicio en 1930, y más allá de las modificaciones que presentó, el Mundial ha sido el escenario de muchos de los momentos más icónicos del fútbol, donde equipos de todas las naciones compiten por la gloria.</p>
            </div>
        </div>
    </div>
    <div class="paises">
        <div class="grafico_paises">
            <iframe title="Mundial 2022" aria-label="Mapa" id="datawrapper-chart-4ppPT" src="https://datawrapper.dwcdn.net/4ppPT/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
            <p class='aclaracion'>*Gales forma parte del Reino Unido con el puesto numero 30</p>
        </div>
        <div class="texto-paises">
            <p>hola</p>
        </div>
    </div>
    <div class="paises">
        <div class="grafico_paises">
            <iframe title="Mundial 1986" aria-label="Map" id="datawrapper-chart-BWQLZ" src="https://datawrapper.dwcdn.net/BWQLZ/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
            <p class='aclaracion'>*Alemania Occidental puesto numero 2</p>
            <p class='aclaracion'>**Escocia forma parte del Reino Unido con puesto 19</p>
            <p class='aclaracion'>***Irlanda del norte con puesto 21</p>
        </div>
        <div class="texto-paises">
            <p>hola</p>
        </div>
    </div>
    <div class="paises">
        <div class="grafico_paises">
            <iframe title="Mundial 1978" aria-label="Map" id="datawrapper-chart-oL8XV" src="https://datawrapper.dwcdn.net/oL8XV/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>

            <p class='aclaracion'>*Alemania Occidental puesto numero 6</p>
            <p class="aclaracion">**Escocia forma parte del Reino Unido con puesto 11</p>
        </div>
        <div class="texto-paises">
            <p>hola</p>
        </div>
    </div> 
</main>



<!-- Estilos CSS -->
<style>
    p{
        font-family: "Quicksand", sans-serif;
        font-optical-sizing: auto;
        font-style: normal;
        color: #2A1552;
    }
    h5{
        font-family: "Quicksand", sans-serif;
        font-optical-sizing: auto;
        font-style: normal;
        font-weight: 700;
        color: #2A1552;
    }
    h2{
        font-family: "Noto Sans KR", sans-serif;
        font-optical-sizing: auto;
        font-weight: 900;
        font-style: normal;
        text-transform: uppercase;
    }
    .intro{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .intro1{
        text-align: center;
        margin-top: 30px;
        margin-bottom: 30px;
    }
    .player{
        width: 30%;
        margin: 5px 0;
    }
    .player img{
        width: 100%;
        height: auto;
    }
    .intro2{
        display: flex;
        justify-content: center;
        padding: 100px 100px;
    }
    .fondo_intro2{
        background-image: url("images/fondo1.png");
        background-size: cover;
        background-position: center;
        height: 150vh; /*Quiero que el tamaño del div tenga el tamaño de la foto de fondo pero no se como, no quiero ajustar manualmente*/
    }
    .texto{
        text-align: center;
        color: #2A1552;
        display: flex;
        flex-direction: column;
        justify-content: center;
        line-height: 35px;
    }
    .paises{
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        flex-direction: row;
        justify-content: center;
    }
    .grafico_paises{
        padding: 0 10px;
        width: 50%;
        height: 70%;
        display: flex; /* Para centrar la imagen dentro de la columna */
        flex-direction: column;
        background-image: url(images/fondo_pais.png); /* Solo para visualización */
        background-size: 100%; /* Ajusta el tamaño de la imagen de fondo al 50% del contenedor */
    }
    .grafico_paises iframe{
        width: 85%;
        height: auto;
    }
    .texto-paises{
        width: 50%;
    }
    .aclaracion{
        font-style: italic;
        font-size: 15px;
        margin: 0;
        color: white;
    }
    .button {
    padding: 10px 20px;
    background-color: #007BFF;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 5px;
  }

  .button:hover {
    background-color: #0056b3;
  }

  .alert-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .alert-box {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    max-width: 500px;
    width: 100%;
    text-align: center;
  }

  .close-button {
    background: none;
    border: none;
    cursor: pointer;
    color: red;
    font-size: 1.2em;
    position: absolute;
    top: 10px;
    right: 10px;
  }

</style>
