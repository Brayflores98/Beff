<!DOCTYPE html>
<html>
<head>
    <title>Obtener ubicación GPS</title>
    <style>
        /* Estilos para centrar el botón en la pantalla */
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        #location {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>

<button onclick="getLocation()">Obtener mi ubicación</button>

<p id="location"></p>

<script>
function getLocation() {
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
    } else {
        document.getElementById("location").innerHTML = "Geolocalización no soportada por este navegador.";
    }
}

function showPosition(position) {
    var lat = position.coords.latitude;
    var lon = position.coords.longitude;
    document.getElementById("location").innerHTML = "Latitud: " + lat + "<br>Longitud: " + lon;
}

function showError(error) {
    switch(error.code) {
        case error.PERMISSION_DENIED:
            document.getElementById("location").innerHTML = "El usuario denegó la solicitud de geolocalización.";
            break;
        case error.POSITION_UNAVAILABLE:
            document.getElementById("location").innerHTML = "La información de ubicación no está disponible.";
            break;
        case error.TIMEOUT:
            document.getElementById("location").innerHTML = "La solicitud de geolocalización ha expirado.";
            break;
        case error.UNKNOWN_ERROR:
            document.getElementById("location").innerHTML = "Ha ocurrido un error desconocido.";
            break;
    }
}
</script>

</body>
</html>
