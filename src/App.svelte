<!-- Script JS -->
<script>
</script>

<!-- Estructura contenido HTML -->
<h1>Representación del consumo de agua en las estaciones</h1>
<div class='container'>
    <div class='item'>
        <img src="./images/dimension25.jpeg" alt="Consumo de agua en invierno (25)">
        <h6>Consumo de agua en verano</h6>
        <p>Magnitud 25</p>
    </div>
    <div class='item'>
        <img src="./images/dimension100.jpeg" alt="Consumo de agua en verano (100)">
        <h6>Consumo de agua en verano</h6>
        <p>Magnitud 100</p>
    </div>
</div>


<!-- Estilos CSS -->
<style>
    img{
        width: 250px;
        height: 250px;
        text-align: center;
    }
    h1{
        font-family: 'Times New Roman', Times, serif;
        font-weight: bold;
        text-align: center;
        text-decoration: underline;
    }
    h6{
        font-size: 20px;
        text-align: center;
    }
    p{
        font-size: 15px;
        text-align: center;
    }
    .item{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .container{
        display: flex;
        justify-content: space-evenly;
    }
</style>
