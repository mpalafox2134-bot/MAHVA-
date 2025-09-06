<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MAHVA - Our Hoodies</title>
  <style>
    /* Reset */
    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
    }

    /* Barra de navegación */
    nav {
      background-color: #6c90a1;
      padding: 15px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    nav h2 { color: white; font-size: 24px; }
    nav a {
      color: white;
      text-decoration: none;
      margin-left: 20px;
      font-size: 16px;
    }
    nav a:hover { text-decoration: underline; }

    /* Encabezado */
    header {
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(to right, #6f7baa, #6b7fab);
      color: white;
    }
    header h1 { font-size: 48px; margin-bottom: 10px; }
    header p { font-size: 18px; }

    /* Botones colecciones */
    .colecciones { text-align: center; margin: 20px; }
    .colecciones button {
      background-color: #6c90a1;
      color: white;
      border: none;
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s;
    }
    .colecciones button:hover { background-color: #7e8cb2; }

    /* Productos */
    .contenedor {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 30px 20px;
    }
    .producto {
      background-color: white;
      border-radius: 15px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
      margin: 15px;
      padding: 20px;
      text-align: center;
      width: 220px;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .producto:hover { transform: translateY(-5px); box-shadow: 0 8px 20px rgba(0,0,0,0.3); }
    .producto img { width: 100%; border-radius: 10px; }
    .producto h2 { font-size: 20px; margin: 15px 0 10px 0; }
    .producto p { color: #555; font-size: 14px; margin-bottom: 15px; }

    .btn-comprar, .btn-ver {
      background-color: #6b95a2;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 10px 15px;
      font-size: 14px;
      cursor: pointer;
      margin: 5px;
      transition: background-color 0.3s;
    }
    .btn-comprar:hover, .btn-ver:hover { background-color: #7e8cb2; }

    /* Carrito */
    #carrito {
      background: white;
      padding: 20px;
      margin: 30px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    }
    #carrito h2 { margin-bottom: 15px; }

    /* Footer */
    footer {
      background-color: #333;
      color: white;
      text-align: center;
      padding: 25px 20px;
      margin-top: 20px;
    }
    footer a { color: white; text-decoration: none; margin: 0 10px; font-size: 18px; }
    footer a:hover { color: #6aa4a0; }
  </style>
</head>
<body>

<!-- Barra de navegación -->
<nav>
  <h2>Mi Tienda</h2>
  <div>
    <a href="#">Inicio</a>
    <a href="#productos">Productos</a>
    <a href="#carrito">Carrito 🛒</a>
  </div>
</nav>

<!-- Encabezado -->
<header>
  <h1>MAHVA</h1>
  <p>OUR HOODIES !!</p>
</header>

<!-- Botones colecciones -->
<div class="colecciones">
  <button onclick="mostrarColeccion('duck')">What the duck</button>
  <button onclick="mostrarColeccion('vangogh')">Van Gogh</button>
  <button onclick="mostrarColeccion('bananas')">Bananas</button>
</div>

<!-- Productos -->
<div class="contenedor" id="productos"></div>

<!-- Carrito -->
<div id="carrito">
  <h2>Tu carrito 🛒</h2>
  <ul id="lista-carrito"></ul>
</div>

<!-- Footer -->
<footer>
  <p>Follow us !!:</p>
  <a href="#">Instagram</a>@MAHVA.APPAREL
  <p>&copy; 2025 OUR HOODIES !!. MARIA Y VALE.</p>
</footer>

<script>
  const colecciones = {
    duck: [
      { id: 1, nombre: "In gray", precio: 45, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/fa5418d870bc4b00b8342074225d81a4.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/2445fa0638eb4c58bd61c372c6850012.png" },
      { id: 2, nombre: "In purple ", precio: 45, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/c63eb43b6ba34c67b25e244b77d63e9e.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/23201f3ee6ec42db96fbb80e5b8cd052.png" },
      { id: 3, nombre: "In blue", precio: 45, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/e1c238014d23485093c033ae1b2ab83e.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/3831f1aebba149f581cb217055b6c9de.png" }

    ],
    vangogh: [
      { id: 4, nombre: "In white", precio: 50, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/937b104f141d436b87b473c99e3ba778.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/5f8a090910a64224a068756bff8861a1.png" },
      { id: 5, nombre: "In black", precio: 50, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/bd18df0fabd844ad88a2ae78b09d72a0.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/6dc4169e00bb4e378e7f7981ab85ec19.png" },
      { id: 6, nombre: "In gray", precio: 50, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/03d5f9a20e814a23a3e25c5425944c43.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/c8854b24ea6b49d28c8418e457eb7c49.png" }
    ],
    bananas: [
      { id: 7, nombre: "In blue", precio: 40, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/faa65f29e7ce48c8bfd6ae0095cd265a.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/152b1b39c70a4d248eb90e2fb0e53953.png" },
      { id: 8, nombre: "In khaki", precio: 40, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/e453159855274869879ba31bbaec9f85.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/32c6a6522f5b47719c4677bc241177b3.png" },
      { id: 9, nombre: "In gray", precio: 40, frente: "https://files.tapstitch.com/hugepod/material/custom_printing/aa2eae61f85144ac9057fd742d0c6947.png", atras: "https://files.tapstitch.com/hugepod/material/custom_printing/c028ac25977c4fcf93cfc258a4bc3825.png" }
    ]
  };

  let carrito = [];

  function mostrarColeccion(nombre) {
    const productos = colecciones[nombre];
    const contenedor = document.getElementById("productos");
    contenedor.innerHTML = "";

    productos.forEach(producto => {
      const div = document.createElement("div");
      div.className = "producto";

      div.innerHTML = `
        <img src="${producto.frente}" alt="${producto.nombre}" id="img-${producto.id}">
        <h2>${producto.nombre}</h2>
        <p>$${producto.precio} USD</p>
        <button class="btn-ver" onclick="verOtraVista(${producto.id}, '${nombre}')">Ver otra vista</button>
        <button class="btn-comprar" onclick="agregarAlCarrito(${producto.id}, '${nombre}')">Añadir al carrito</button>
      `;
      contenedor.appendChild(div);
    });
  }

  function verOtraVista(id, coleccion) {
    const producto = colecciones[coleccion].find(p => p.id === id);
    const img = document.getElementById(`img-${id}`);
    if (img.src.includes(producto.frente)) {
      img.src = producto.atras;
    } else {
      img.src = producto.frente;
    }
  }

  function agregarAlCarrito(id, coleccion) {
    const producto = colecciones[coleccion].find(p => p.id === id);
    carrito.push(producto);
    actualizarCarrito();
  }

  function actualizarCarrito() {
    const lista = document.getElementById("lista-carrito");
    lista.innerHTML = "";
    carrito.forEach(item => {
      const li = document.createElement("li");
      li.textContent = `${item.nombre} - $${item.precio} USD`;
      lista.appendChild(li);
    });
  }
</script>

</body>
</html>
