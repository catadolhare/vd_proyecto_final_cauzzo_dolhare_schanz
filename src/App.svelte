<!-- Script JS -->
<script>
    import Scroller from "@sveltejs/svelte-scroller";
    import * as d3 from "d3";
    import { onMount } from "svelte";
    let datos=[];
    import { scaleOrdinal } from 'd3-scale';
    import * as d3 from "d3";

    import {LayerCake, Svg} from "layercake";

    import Key from './_components/Key.html.svelte';
    import AxisX from './_components/AxisX.svelte';
    import Beeswarm from './_components/Beeswarm.svelte';

    let jugadores = [];

    const r = 12;

    const xKey1 = "posicion";
    const xKey2 = "pais";
    const xKey3 = "partidos_jugados";
    const xKey4 = "goles";
    const xKey5 = "mundiales";
    const xKey6 = "cantidad_mundiales"
    const zKey = "año";

    const coloresAño = ['#FAFF00', '#80F6FF', '#2A1552'];

    /* Variables para el scroller1 */
    let count
    let index
    let offset
    let progress
    let top = 0.1
    let threshold = 0.5
    let bottom = 0.9
    
    /* Variables para el scroller 2 */
    let count2
    let index2
    let offset2
    let progress2
    let top2 = 0.1
    let threshold2 = 0.5
    let bottom2 = 0.9

    /* Variables para el scroller 3 */
    let count3
    let index3
    let offset3
    let progress3
    let top3 = 0.1
    let threshold3 = 0.5
    let bottom3 = 0.9

    /* Variables para el scroller 4 */
    let count4
    let index4
    let offset4
    let progress4
    let top4 = 0.1
    let threshold4 = 0.5
    let bottom4 = 0.9

    /* Variables para el scroller 4 */
    let count4
    let index4
    let offset4
    let progress4
    let top4 = 0.1
    let threshold4 = 0.5
    let bottom4 = 0.9

    let showInfo = false;
    let jugadorInfo= false;
    let selectedJugador = null;
    function toggleInfo() {
        showInfo = !showInfo;
    }
    function toggleInfoJ(jugador) {
        jugadorInfo = !jugadorInfo;
        // Actualiza selectedJugador solo si se proporciona un jugador
        if (jugador) {
            selectedJugador = jugador;
        } else {
            selectedJugador = null; // Limpiar selectedJugador si no se proporciona un jugador
        }
        
    }
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
    function getImagePath(jugador){
        return jugador.imagen;
    }
    onMount(() => {
        d3.csv("./datos_generales.csv", d3.autoType).then((data) => {
            datos = data;
            console.log(datos);
            datos.forEach(jugador => {
                console.log(jugador);
                getImagePath(jugador);
            });
        });
    });

    onMount(() => {
    d3.csv("./jugadores.csv", d3.autoType).then(data => {
        jugadores = data;
        });
    });


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
                            <img src="images/pausa_blanco.png" alt="Pause" style="width:20px; height:20px;">
                        {/if}
                    </button>
                    <button class="control-button" on:click={toggleInfo}>
                        <img src="images/lista.png" alt="Menu" style="width:20px; height:20px;">
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
        <Scroller
        top={top}
        threshold={threshold}
        bottom={bottom}
        bind:count={count}
        bind:index={index}
        bind:offset={offset}
        bind:progress={progress}
        >
            <div slot="background" class="background-scroller">
                <div class="imagen-año">
                    <img src="images/1978.png" alt="1978" style="width:800px;">
                </div>
            </div>
            <div slot="foreground" class="foreground_container">
                <section class="step_foreground">
                    <div class="info-año">
                        <p>César Luis Menotti convocó a 22 jugadores para el Mundial de 1978, haciendo una selección que combinaba experiencia y juventud. Su predilecto 4-3-3, combinado con el rendimiento del plantel fue la llave con la que Argentina abrió las puertas del campeonato.</p>
                        <img src="images/tipito1978.png" alt="">
                    </div>
                </section>
                <section class="step_foreground">
                    <div class="equipo-container">
                        {#each datos as jugador}
                            {#if jugador.anio===1978}
                                <div class="futbolista">
                                    <img src={getImagePath(jugador)} alt={jugador.nombre} style="width:100px; height:auto;">
                                </div>
                            {/if}
                        {/each}
                    </div>
                </section>
            </div>
        </Scroller>

        <Scroller
        top={top2}
        threshold={threshold2}
        bottom={bottom2}
        bind:count={count2}
        bind:index={index2}
        bind:offset={offset2}
        bind:progress={progress2}
        >
            <div slot="background" class="background-scroller">
                <div class="imagen-año">
                    <img src="images/1986.png" alt="1986" style="width:800px;">
                </div>
            </div>
            <div slot="foreground" class="foreground_container">
                <section class="step_foreground">
                    <div class="info-año">
                        <p>Los 22 elegidos de Carlos Salvador Bilardo para el mundial 1986 reflejaron su meticulosa y estratégica visión del fútbol. Apostó por un plantel que combinaba talento, disciplina y una fuerte mentalidad competitiva. Esta selección, aunque inicialmente cuestionada por algunos críticos, demostró ser perfecta para ejecutar su esquema táctico, llevando a Argentina a conquistar su segundo campeonato mundial.</p>
                        <img src="images/tipito1986.png" alt=""> <!--Esta hay que acomodar posicion-->
                    </div>
                </section>
                
                <section class="step_foreground">
                    <div class="equipo-container">
                        {#each datos as jugador}
                            {#if jugador.anio===1986}
                                <div class="futbolista">
                                    <img src={getImagePath(jugador)} alt={jugador.nombre} style="width:100px; height:auto;">
                                </div>
                            {/if}
                        {/each}
                    </div>
                </section>
                
            </div>
        </Scroller>

        <Scroller
        top={top3}
        threshold={threshold3}
        bottom={bottom3}
        bind:count={count3}
        bind:index={index3}
        bind:offset={offset3}
        bind:progress={progress3}
        >
            <div slot="background" class="background-scroller">
                <div class="imagen-año">
                    <img src="images/2022.png" alt="2022" style="width:800px;">
                </div>
            </div>
            <div slot="foreground" class="foreground_container">
                <section class="step_foreground">
                    <div class="info-año">
                        <p>La Selección de Scaloni, también llamada "Scaloneta", para el Mundial de 2022 destacó por su diversidad y equilibrio. Lionel Scaloni seleccionó a 26 jugadores, combinando experiencia y juventud. Con un enfoque en la cohesión y el espíritu de equipo, Scaloni logró formar un grupo compacto y versátil.</p>
                        <img src="images/tipito2022.png" alt="">
                    </div>
                </section>
                
                <section class="step_foreground">
                        <div class="equipo-container">
                                <div class="equipo">
                                    {#each datos as jugador}
                                        {#if jugador.anio===2022}
                                            <button class="futbolista" on:click={() => toggleInfoJ(jugador)}>
                                                <img src={getImagePath(jugador)} alt={jugador.nombre} style="width:75px; height:auto;">
                                            </button>
                                        {/if}
                                    {/each}
                                </div>
                                <div class="info-futbolista">
                                    {#each datos as jugador}
                                        {#if selectedJugador === jugador}
                                            <div class="info">
                                                {#if selectedJugador.anio===2022}
                                                    <div class="foto_futbol">
                                                        <img src={getImagePath(selectedJugador)} alt={selectedJugador.nombre}>
                                                    </div>
                                                    <h4>{selectedJugador.nombre}</h4>
                                                    <p style="color:white;">{selectedJugador.posicion}</p>
                                                    <p style="color:white;">{selectedJugador.club}</p>
                                                    
                                                {/if}
                                                <button class="close_info" on:click={toggleInfoJ}>
                                                    <img src="images/cruz_blanca.png" alt="Cerrar">
                                                </button>
                                            </div>
                                        {/if}
                                    {/each}
                                </div>
                        </div>
                </section>
            </div>
        </Scroller>

    </div>
    <div class="analisis">
        <div class="titulo">
            <div class="info-titulo">
                <h2>Cada selección, una catedra de fútbol...</h2>
                <p>Para comprender cómo cada una de estas selecciones se hizo con la copa debemos conocer las estadísticas detalladas de su desempeño. Analizaremos los partidos jugados por cada jugador, los goles anotados, las posiciones en el campo, las ligas de las que venían y las tarjetas recibidas. Esto nos permitirá desglosar las estrategias de cada DT, revelando cómo cada entrenador maximizó el potencial de sus jugadores. A través de esta comparación, podremos identificar los elementos clave que llevaron a Argentina al éxito en los Mundiales de 1978, 1986 y 2022, destacando las similitudes y diferencias en su camino hacia la gloria.</p>
            </div>
            <img src="images/gol.png" alt="">
        </div>
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Posiciones</h3>
                        <div class="grafico">
                            <!--Posicion-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey1}
                                z={zKey}
                                xScale={d3.scaleBand()}
                                zScale={d3.scaleOrdinal()}
                                xDomain={["Arquero", "Defensor", "Mediocampista", "Delantero"]}
                                zRange={coloresAño}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={5}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
        </div>
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Liga en la que juegan</h3>
                        <div class="grafico">
                            <!--Liga donde juegan-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey2}
                                z={zKey}
                                xScale={d3.scaleBand()}
                                zScale={d3.scaleOrdinal()}
                                xDomain={["Argentina", "España", "Italia", "Francia", "Inglaterra", "Portugal", "Mexico/USA"]}
                                zRange={coloresAño}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={7}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                                
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
        </div>
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Partidos jugados en el mundial</h3>
                        <div class="grafico">
                            <!--Partidos jugados-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey3}
                                z={zKey}
                                zRange={coloresAño}
                                zScale={d3.scaleOrdinal()}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={7}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                                
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
        </div>
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Goles anotados en el mundial</h3>
                        <div class="grafico">
                            <!--Goles-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey4}
                                z={zKey}
                                zRange={coloresAño}
                                zScale={d3.scaleOrdinal()}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={7}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                                
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
        </div>
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Debut mundialista</h3>
                        <div class="grafico">
                            <!--Debut mundialista-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey5}
                                z={zKey}
                                xScale={d3.scaleBand()}
                                zScale={d3.scaleOrdinal()}
                                zRange={coloresAño}
                                xDomain={["Debut mundialista", "Ya jugaron un mundial"]}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={7}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                                
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
        </div>
        
        <div class="grafico-scroller">
            <Scroller
                top={top}
                threshold={threshold}
                bottom={bottom}
                bind:count={count}
                bind:index={index}
                bind:offset={offset}
                bind:progress={progress}
                >
                    <div slot="background" class="background-scroller">
                        <h3>Cantidad de mundiales jugados</h3>
                        <div class="grafico">
                            <!--Cantidad mundiales-->
                            <LayerCake
                                padding={{bottom: 15}}
                                x={xKey6}
                                z={zKey}
                                zRange={coloresAño}
                                zScale={d3.scaleOrdinal()}
                                data={jugadores}
                            >
                
                                <Svg>
                                    <AxisX
                                        baseline
                
                                    />
                                    <Beeswarm
                                        r={r}
                                        spacing={7}
                                        getTitle={d => `${d["nombre"]}`}
                                    />
                                </Svg>
                                
                            </LayerCake>
                        </div>
                    </div>
                    <div slot="foreground" class="foreground_container">
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                        <section class="step_foreground-analisis">
                            <div class="foreground-analisis">
                                <p>...</p>
                            </div>
                        </section>
                    </div>
            </Scroller>
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
    .grafico{
        width: 85%;
        height: 500px;
    }
    .step_foreground-analisis{
        display: flex;
        justify-content: end;
        align-items: center;
        height: 90vh;
    }
    .foreground-analisis{
        width: 300px;
        height: 150px;
        background-color: red;
    }
    p{
        font-family: "Quicksand", sans-serif;
        font-optical-sizing: auto;
        font-style: normal;
        color: #2A1552;
        font-size: 20px;
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
        font-size: 30px;
        text-transform: uppercase;
    }
    h4{
        font-family: "Fredoka", sans-serif;
        font-optical-sizing: auto;
        font-weight: 700;
        font-style: normal;
        font-variation-settings:
            "wdth" 100;
        font-size: 30px;
        color: #FAFF00;
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
        font-size: 50px;
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
    .protagonistas h2{
        background-color: #84DFED;
        margin:0;
        padding-top: 30px;
    }
    .protagonistas1978{
        background-color: #84DFED;
    }
    .protagonistas2022{
        background-color: #84DFED;
    }
    .background-scroller{
        height: 85vh;
    }
    .step_foreground{
        margin: 0px 100px 10px 100px;
        height: 90vh;
        display: flex;
        align-items: center;
    }
    .imagen-año{
        max-width: 560px;
        margin: 0px 100px 10px 100px;
        height: 85vh;
        display: flex;
        align-items: center;
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
    .equipo-container{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
    }
    .equipo{
        width: 80%;
    }
    .futbolista{
        background-color:#2A1552;
        display: flex;
        margin: 5px;
        overflow: hidden;
        border-radius: 50%;
        padding: 5px 10px;
        cursor: pointer;
        align-content: center;
        border: none;
    }
    .info-futbolista{
        width: 20%;
        align-items: center;   
    }
    .info{
        padding: 5px 10px;
        border-radius: 10px;
        background-color: #2A1552;
        height:80%;
    }
    .foto_futbol{
        width:70%;
        height: auto;
        border-radius: 10px;   
    }
    .foto_futbol img{
        width:100px;
    }
    .close_info{
        width:10%;
        
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