<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tienda de ropa- modasbayola
    
    
  </title>
    <style>
        /* Estilos generales */
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(to right, #2c3e50, #4ca1af);
            color: white;
            text-align: center;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 500px;
            margin: 50px auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        h1, h2, h3 {
            color: #ffdd00;
        }

        .form {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .form input {
            width: 95%;
            padding: 12px;
            margin: 5px auto;
            border-radius: 5px;
            border: none;
            outline: none;
            font-size: 16px;
            background: rgba(255, 255, 255, 0.8);
        }

        button {
            background: #ffdd00;
            color: black;
            padding: 12px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
            font-size: 16px;
            transition: 0.3s;
        }

        button:hover {
            background: #ffbb00;
            transform: scale(1.05);
        }

        ul {
            list-style: none;
            padding: 0;
            margin: 20px 0;
        }

        ul li {
            background: rgba(255, 255, 255, 0.2);
            padding: 12px;
            margin: 5px;
            border-radius: 5px;
            font-size: 16px;
        }

        .resumen {
            margin-top: 20px;
        }

        @media (max-width: 600px) {
            .container {
                width: 90%;
                margin: 30px auto;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>tienda de ropa-modasbayola</h1>

        <div class="form">
            <input type="text" id="producto" placeholder="Ej: Camiseta, Mate, Souvenir">
            <input type="number" id="cantidad" placeholder="Cantidad vendida">
            <input type="number" id="precio" placeholder="Precio unitario (ARS)">
            <button onclick="registrarVenta()">Registrar Venta</button>
        </div>

        <h2>Ventas del Día</h2>
        <ul id="lista-ventas"></ul>

        <div class="resumen">
            <h3>Total Ganado Hoy: <span id="total">0</span> ARS</h3>
            <button onclick="finalizarDia()">Finalizar Día</button>
        </div>
    </div>

    <script>
        let totalGanado = 0;

        function registrarVenta() {
            let producto = document.getElementById("producto").value;
            let cantidad = parseFloat(document.getElementById("cantidad").value);
            let precio = parseFloat(document.getElementById("precio").value);

            if (producto === "" || isNaN(cantidad) || isNaN(precio) || cantidad <= 0 || precio <= 0) {
                alert("Por favor, ingrese datos válidos.");
                return;
            }

            let totalVenta = cantidad * precio;
            totalGanado += totalVenta;

            let lista = document.getElementById("lista-ventas");
            let item = document.createElement("li");
            item.textContent = `${cantidad}x ${producto} - ${totalVenta} ARS`;
            lista.appendChild(item);

            document.getElementById("total").textContent = totalGanado;

            // Limpiar campos
            document.getElementById("producto").value = "";
            document.getElementById("cantidad").value = "";
            document.getElementById("precio").value = "";
        }

        function finalizarDia() {
            alert(`Ganancia total del día: ${totalGanado} ARS`);
            location.reload();
        }
    </script>
</body>
</html>
