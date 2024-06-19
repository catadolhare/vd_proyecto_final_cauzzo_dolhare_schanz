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
    let audio;
    let isPlayingWakawaka = false, isPlayingEstateItaliana = false, isPlayingWeareone = false, isPlayingLacopavida = false;
    let audioEstateItaliana, audioWakawaka, audioWeareone, audioLacopavida;
    let currentAudio = null;
    let showFloatingControl = false;
    let isPaused = true;

    function playAudio(audioElement, setIsPlaying, isPlaying) {
        if (currentAudio && currentAudio !== audioElement) {
            currentAudio.pause();
            setIsPlaying(false);
        }
        if (audioElement.paused) {
            audioElement.play();
            setIsPlaying(true);
            currentAudio = audioElement;
            isPaused = false;
        } else {
            audioElement.pause();
            setIsPlaying(false);
            currentAudio = null;
            isPaused = true;
        }
        showFloatingControl = true;
    }
    
    function stopAllAudio() {
        if (audioWakawaka) audioWakawaka.pause();
        if (audioEstateItaliana) audioEstateItaliana.pause();
        if (audioWeareone) audioWeareone.pause();
        if (audioLacopavida) audioLacopavida.pause();
        isPlayingWakawaka = isPlayingEstateItaliana = isPlayingWeareone = isPlayingLacopavida = false;
        currentAudio = null;
        isPaused = true;
    }

</script>
<main>
    <audio bind:this={audioWakawaka} src="canciones/wakawaka.mp3"></audio>
    <audio bind:this={audioEstateItaliana} src="canciones/estate_italiana.mp3"></audio>
    <audio bind:this={audioWeareone} src="canciones/we_are_one.mp3"></audio>
    <audio bind:this={audioLacopavida} src="canciones/la_copa_vida.mp3"></audio>
    <head>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300..700&display=swap" rel="stylesheet">

        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@300..700&display=swap" rel="stylesheet">
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
        
            <button class="button" on:click={toggleInfo}>
                <h5 style="color: #DBED0B; font-style: bold;">Tocá para musicalizar</h5>
            </button>
            {#if showInfo}
                <div class="alert-overlay">
                    <div class="alert-box">
                        <div class="canciones">
                            <div class="foto_canciones">
                                <img src="images/shakira.jpg" alt="shakira">
                            </div>
                            <div class="cancion-artista">
                                <h2>Waka Waka</h2>
                                <p>Shakira</p>
                            </div>
                            <div class="boton_cancion">
                                <button class="button_canciones" on:click={() => playAudio(audioWakawaka, (playing) => isPlayingWakawaka = playing)}>
                                    {#if isPlayingWakawaka}
                                        <img src="images/pausa_violeta.png" alt="Pause" style="width:25px; height:25px;">
                                    {:else}
                                        <img src="images/play_violeta.png" alt="Play" style="width:25px; height:25px;">
                                    {/if}
                                </button>
                            </div>
                        </div>
                        <div class="canciones">
                            <div class="foto_canciones">
                                <img src="images/gianna.jpg" alt="GiannaEdoardo">
                            </div>
                            <div class="cancion-artista">
                                <h2>Un'Estate Italiana</h2>
                                <p>Gianna Nannini & Edoardo Bennato</p>
                            </div>
                            <div class="boton_cancion">
                                <button class="button_canciones" on:click={() => playAudio(audioEstateItaliana, (playing) => isPlayingEstateItaliana = playing)}>
                                    {#if isPlayingEstateItaliana}
                                        <img src="images/pausa_violeta.png" alt="Pause" style="width:25px; height:25px;">
                                    {:else}
                                        <img src="images/play_violeta.png" alt="Play" style="width:25px; height:25px;">
                                    {/if}
                                </button>
                            </div>
                        </div>
                        <div class="canciones">
                            <div class="foto_canciones">
                                <img src="images/pitbull.jpg" alt="pitbull">
                            </div>
                            <div class="cancion-artista">
                                <h2>We are one</h2>
                                <p>Pitbull, Jennifer Lopez & Claudia Leitte</p>
                            </div>
                            <div class="boton_cancion">
                                <button class="button_canciones" on:click={() => playAudio(audioWeareone, (playing) => isPlayingWeareone = playing)}>
                                    {#if isPlayingWeareone}
                                        <img src="images/pausa_violeta.png" alt="Pause" style="width:25px; height:25px;">
                                    {:else}
                                        <img src="images/play_violeta.png" alt="Play" style="width:25px; height:25px;">
                                    {/if}
                                </button>
                            </div>
                        </div>
                        <div class="canciones">
                            <div class="foto_canciones">
                                <img src="images/ricky.jpg" alt="Ricky">
                            </div>
                            <div class="cancion-artista">
                                <h2>La copa de la vida</h2>
                                <p>Ricky Martin</p>
                            </div>
                            <div class="boton_cancion">
                                <button class="button_canciones" on:click={() => playAudio(audioLacopavida, (playing) => isPlayingLacopavida = playing)}>
                                    {#if isPlayingLacopavida}
                                        <img src="images/pausa_violeta.png" alt="Pause" style="width:25px; height:25px;">
                                    {:else}
                                        <img src="images/play_violeta.png" alt="Play" style="width:25px; height:25px;">
                                    {/if}
                                </button>
                            </div>
                        </div>
                        <button class="button" on:click={toggleInfo}>Cerrar</button>
                    </div>
                </div>
            {/if}

            {#if showFloatingControl}
                <div class="floating-control">
                    <button class="control-button" on:click={stopAllAudio}>
                        {#if isPaused}
                            <img src="images/play_blanco.png" alt="Play" style="width:20px; height:20px;">
                        {:else}
                            <img src="images/pausa_blanco.png" alt="Pause" style="width:25px; height:25px;">
                        {/if}
                    </button>
                    <button class="control-button" on:click={toggleInfo}>
                        <p style="color:white; font-size: 14px;">Menu</p>
                    </button>
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
    <div class="mundiales">
        <h2>El mundo unido por una pasión</h2>
        <div class="paises">
            <div class="grafico_paises">
                <iframe title="Mundial 1978" aria-label="Map" id="datawrapper-chart-oL8XV" src="https://datawrapper.dwcdn.net/oL8XV/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
    
                <p class='aclaracion'>*Alemania Occidental puesto numero 6</p>
                <p class="aclaracion">**Escocia forma parte del Reino Unido con puesto 11</p>
            </div>
            <div class="info-mundial">
                <div class="texto-paises">
                    <h3>1978</h3>
                    <p>, contó con la participación de 16 países. Este torneo fue notable por la gran competencia y el ambiente festivo que se vivió. Argentina se coronó campeona del mundo por primera vez en su historia, tras vencer a Países Bajos en el Monumental.</p>
                </div>
                <img src="images/foto1978.png" alt="">
            </div>
            
        </div>
        <div class="paises">
            <div class="info-mundial">
                <div class="texto-paises">
                    <h3>1986</h3>
                    <p>, celebrado en México, reunió a 24 equipos de diversas partes del mundo. Este torneo es recordado por las actuaciones estelares de Diego Maradona, incluyendo su famoso "Gol del Siglo" y la "Mano de Dios". Argentina venció a Alemania y se consgró campeona nuevamente. </p>
                </div>
                <img src="images/foto1986.png" alt="">
            </div>
            <div class="grafico_paises">
                <iframe title="Mundial 1986" aria-label="Map" id="datawrapper-chart-BWQLZ" src="https://datawrapper.dwcdn.net/BWQLZ/2/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
                <p class='aclaracion'>*Alemania Occidental puesto numero 2</p>
                <p class='aclaracion'>**Escocia forma parte del Reino Unido con puesto 19</p>
                <p class='aclaracion'>***Irlanda del norte con puesto 21</p>
            </div>
        </div>
        <div class="paises">
            <div class="grafico_paises">
                <iframe title="Mundial 2022" aria-label="Mapa" id="datawrapper-chart-4ppPT" src="https://datawrapper.dwcdn.net/4ppPT/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="294" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();</script>
                <p class='aclaracion'>*Gales forma parte del Reino Unido con el puesto numero 30</p>
            </div>
            <div class="info-mundial">
                <div class="texto-paises">
                    <h3>2022</h3>
                    <p>, organizado en Qatar, el primer torneo mundialista realizado en el Medio Oriente y durante los meses de noviembre y diciembre, con 32 selecciones, notable por sus innovaciones tecnológicas y su enfoque en la sostenibilidad. Argentina se coronó campeona por tercera vez, venciendo a Francia en una final épica.</p>
                </div>
                <img src="images/foto2022.png" alt="">
            </div>
        </div>
    </div>
    <div class="protagonistas">
        <h2>Los Protagonistas...</h2>
        <div class="protagonistas-año">
            <div class="imagen-año">
                <img src="images/1978.png" alt="1978">
            </div>
            <div class="info-año">
                <p>César Luis Menotti convocó a 22 jugadores para el Mundial de 1978, haciendo una selección que combinaba experiencia y juventud. Su predilecto 4-3-3, combinado con el rendimiento del plantel fue la llave con la que Argentina abrió las puertas del campeonato.</p>
                <img src="images/tipito1978.png" alt="">
            </div>
        </div>
        <div class="protagonistas-año">
            <div class="imagen-año">
                <img src="images/1986.png" alt="1978">
            </div>
            <div class="info-año">
                <p>Los 22 elegidos de Carlos Salvador Bilardo para el mundial 1986 reflejaron su meticulosa y estratégica visión del fútbol. Apostó por un plantel que combinaba talento, disciplina y una fuerte mentalidad competitiva. Esta selección, aunque inicialmente cuestionada por algunos críticos, demostró ser perfecta para ejecutar su esquema táctico, llevando a Argentina a conquistar su segundo campeonato mundial.</p>
                <img src="images/tipito1986.png" alt=""> <!--Esta hay que acomodar posicion-->
            </div>
        </div>
        <div class="protagonistas-año">
            <div class="imagen-año">
                <img src="images/2022.png" alt="1978">
            </div>
            <div class="info-año">
                <p>La Selección de Scaloni, también llamada "Scaloneta", para el Mundial de 2022 destacó por su diversidad y equilibrio. Lionel Scaloni seleccionó a 26 jugadores, combinando experiencia y juventud. Con un enfoque en la cohesión y el espíritu de equipo, Scaloni logró formar un grupo compacto y versátil.</p>
                <img src="images/tipito2022.png" alt="">
            </div>
        </div>
    </div>
    <div class="analisis">
        <div class="titulo">
            <div class="info-titulo">
                <h2>Cada selección, una catedra de fútbol...</h2>
                <p>Para comprender cómo cada una de estas selecciones se hizo con la copa debemos conocer las estadísticas detalladas de su desempeño. Analizaremos los partidos jugados por cada jugador, los goles anotados, las posiciones en el campo, las ligas de las que venían y las tarjetas recibidas. Esto nos permitirá desglosar las estrategias de cada DT, revelando cómo cada entrenador maximizó el potencial de sus jugadores. A través de esta comparación, podremos identificar los elementos clave que llevaron a Argentina al éxito en los Mundiales de 1978, 1986 y 2022, destacando las similitudes y diferencias en su camino hacia la gloria.</p>
            </div>
            <img src="images/gol.png" alt="">
        </div>
        
    </div>
    <div class="footer">
        <p>Camila Cauzzo</p>
        <p>Catalina Dolhare</p>
        <p>Joaquin Schanz</p>
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
        font-family: "Fredoka", sans-serif;
        font-optical-sizing: auto;
        font-weight: 700;
        font-style: normal;
        font-variation-settings:
            "wdth" 100;
        text-transform: uppercase;
        text-align: center;
        font-size: 40px;
        color: #2A1552;
    }
    h3{
        font-family: "Fredoka", sans-serif;
        font-optical-sizing: auto;
        font-weight: 700;
        font-style: normal;
        font-variation-settings:
            "wdth" 100;
        font-size: 50px;
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
        height: 50vh;
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
        height: 150vh;
    }
    .texto{
        text-align: center;
        color: #2A1552;
        display: flex;
        flex-direction: column;
        justify-content: center;
        line-height: 35px;
    }
    .mundiales{
        padding-top: 30px;
    }
    .paises{
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        flex-direction: row;
        justify-content: center;
        margin: 10px 100px;
        padding: 10px 0;
    }
    .grafico_paises{
        padding: 0 20px;
        width: 50%;
        height: 70%;
        display: flex; /* Para centrar la imagen dentro de la columna */
        flex-direction: column;
        background-image: url(images/fondo_paises.png); /* Solo para visualización */
        margin: 0 10px;
        background-size: 100%; /* Ajusta el tamaño de la imagen de fondo al 50% del contenedor */
    }
    .grafico_paises iframe{
        width: 85%;
        height: auto;
        margin-top: 40px;
    }
    .info-mundial{
        width: 50%;
        margin: 0 10px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .texto-paises h3{
        display: inline;
        color: #FAFF00;
        
    }
    .texto-paises p{
        display: inline;
        line-height: 35px;
    }
    .info-mundial img{
        width: 50%;
        height: auto;
    }
    .aclaracion{
        font-style: italic;
        font-size: 15px;
        margin: 0;
        color: white;
    }
    .button {
        padding: 10px 20px;
        background-color:  #2A1552;
        color: white;
        border: none;
        cursor: pointer;
        border-radius: 5px;
        align-content: center;
        margin-top: 20px;

    }

    .button:hover {
        background-color:#007BFF;
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
        background-color:#2A1552;
    }
    .canciones{
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 10px 0;
        background-color: white;
        border-radius: 10px;
        height:50%;
    }
    .foto_canciones{
        width:20%;
        height: auto;
        border-radius: 10px;
        margin-bottom: 5px;
        margin-top: 5px;
    }
    .foto_canciones img{
        width:80px;
        height: 80px;
        border-radius: 50%;
    }
    .cancion-artista{
        width: 65%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .cancion-artista h2{
        font-size: 30px;
        margin: 0;
    }
    .cancion-artista p{
        margin: 0;
    }
    .boton_cancion{
        width:15%;
        height: auto;
        
    }
    .button_canciones {
        padding: 5px 10px;
        background-color: white;
        cursor: pointer;
        border-radius: 5px;
        align-content: center;
        border: none;
    }
    .floating-control {
        position: fixed;
        bottom: 20px;
        right: 20px;
        display: flex;
        flex-direction: column;
        gap: 10px;
        z-index: 1000;
        align-items: center;
    }

    .control-button {
        background-color: #2A1552;
        border: none;
        border-radius: 50%;
        padding: 10px;
        cursor: pointer;
    }

    .control-button img {
        width: 25px;
        height: 25px;
    }

    .control-button:hover {
        background-color: #007BFF;
    }
    .protagonistas{
        margin: 10px 100px;
    }
    .protagonistas-año{
        display: flex;
        justify-content: flex-start;
        align-items: center;
    }
    .imagen-año{
        position: absolute;
        width: 45%;
    }
    .imagen-año img{
        width: 100%;
        height: auto;
    }
    .info-año{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        position: relative;
    }
    .info-año img{
        width: 25%;
        height: auto;
    }
    .titulo{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .titulo img{
        width:12.5%;
    }
    .analisis{
        margin: 10px 100px;
    }
    .info-titulo{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .footer{
        display: flex;
        justify-content: space-around;
        align-items: center;
        background-color: #2A1552;
        height: 10vh;
    }
    .footer p{
        color: white;
        margin: 0;
    }
</style>
