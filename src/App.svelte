<!-- Script JS -->
<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import { onMount } from "svelte";
    let count, index, offset, progress;
    let top = 0.1, threshold = 0.5, bottom = 0.9;
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
            <img src="https://t3.ftcdn.net/jpg/05/03/75/98/360_F_503759828_kadMu7Zxbk9jNrZE1JjFfVwkkgxqe6KS.jpg" alt="Player">
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
        background-color: aliceblue;
    }
    .grafico_paises{
        padding: 0 10px;
        width: 50%;
        display: flex; /* Para centrar la imagen dentro de la columna */
        flex-direction: column;
        background-image: url(images/fondo_paises.png); /* Solo para visualización */
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
</style>
