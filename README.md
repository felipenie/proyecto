[Uploading CSS…<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CANSERBERO.WEB</title>
    <link rel="stylesheet" href="./CSS/style.css">
    
      <nav>
  <ul>
      <li><a href="#inicio">Inicio</a></li>
      <li><a href="#biografia">Biografía</a></li>
      <li><a href="#musica">Música</a></li>
      <li><a href="#galeria">Galería</a></li>
      <li><a href="#contacto">Contacto</a></li>
  </ul>
</nav>



    </style>
    <style>
        /* Estilos básicos */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #333;
            color: white;
            display: flex;
            justify-content: center; /* Centra el contenido horizontalmente */
            align-items: center; /* Centra el contenido verticalmente */
            padding: 10px 20px;
        }

        header img {
            width: 50px; /* Ajusta el tamaño de la imagen */
            height: auto;
            margin-right: 20px; /* Añade espacio entre la imagen y el título */
        }

        header h1 {
            margin: 0;
            font-size: 2rem; /* Ajusta el tamaño del título */
        }

        nav {
            background-color: #332710;
            overflow: hidden;
        }

        nav a {
            color: rgb(236, 236, 236);
            padding: 14px 20px;
            text-decoration: none;
            display: inline-block;
        }

        nav a:hover {
            background-color: #ddd;
            color: black;
        }

        /* Estilos para las ventanas modales */
        .modal {
            display: none; /* Oculto por defecto */
            position: fixed;
            z-index: 1; /* Se asegura de estar encima de todo */
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.4); /* Fondo semitransparente */
            padding-top: 60px;
        }

        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
        }

        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }

        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }

        /* Estilos para la bandeja de opiniones */
        .opinion-form {
            margin-top: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .opinion-form input,
        .opinion-form textarea {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ddd;
        }

        .opinion-form button {
            padding: 10px 20px;
            border: none;
            background-color: #28a745;
            color: white;
            cursor: pointer;
            border-radius: 5px;
        }

        .opinion-form button:hover {
            background-color: #218838;
        }

        .opinions-list {
            margin-top: 20px;
        }

        .opinion {
            background-color: #f9f9f9;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 5px;
            box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
        }

        .opinion p {
            font-size: 1rem;
            color: #333;
        }

        .opinion .author {
            font-weight: bold;
            color: #555;
        }

        .opinion .date {
            font-size: 0.9rem;
            color: #888;
        }

        .opinion .votes {
            margin-top: 10px;
        }

        .vote-button {
            padding: 5px 10px;
            border: none;
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border-radius: 5px;
            margin-right: 10px;
        }

        .vote-button:hover {
            background-color: #0056b3;
        }

        .vote-count {
            font-size: 1.1rem;
            font-weight: bold;
        }
    </style>
</head>
<body>

<header>
    
    <h1>CANSERBERO</h1>
</header>

<nav>
    <a href="javascript:void(0);" onclick="openModal('registroModal')">Registro/Inicio de Sesión</a>
    <a href="javascript:void(0);" onclick="openModal('productosModal')">Álbumes</a>
    <a href="javascript:void(0);" onclick="openModal('servicioModal')">Bandeja de opiniones</a>
    <a href="javascript:void(0);" onclick="openModal('informacionModal')">Información</a>
</nav>

<!-- Ventana Modal para Registro/Inicio de Sesión -->
<div id="registroModal" class="modal">
  <div class="modal-content">
      <span class="close" onclick="closeModal('registroModal')">&times;</span>
      <h2>REGISTRO/INICIO DE SESIÓN</h2>
      <form id="registroForm">
          <label for="username">Nombre de usuario:</label>
          <input type="text" id="username" name="username" placeholder="Ingresa tu nombre de usuario" required>
          
          <label for="email">Correo electrónico:</label>
          <input type="email" id="email" name="email" placeholder="Ingresa tu correo electrónico" required>
          
          <label for="password">Contraseña:</label>
          <input type="password" id="password" name="password" placeholder="Ingresa tu contraseña" required>
          
          <button type="submit">Registrarse</button>
      </form>
  </div>
</div>

<!-- Ventana Modal para Bandeja de Opiniones -->
<div id="servicioModal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal('servicioModal')">&times;</span>
        <h2>BANDEJA DE OPINIONES</h2>

        <!-- Formulario para dejar una opinión -->
        <div class="opinion-form">
            <input type="text" id="author" placeholder="Tu nombre" required>
            <textarea id="opinionText" rows="4" placeholder="Deja tu opinión..." required></textarea>
            <button onclick="addOpinion()">Enviar Opinión</button>
        </div>

        <!-- Lista de opiniones -->
        <div class="opinions-list" id="opinionsList">
            <!-- Las opiniones se agregarán aquí dinámicamente -->
        </div>
    </div>
</div>

<!-- Ventana Modal para Álbumes -->
<div id="productosModal" class="modal">
  <div class="modal-content">
      <span class="close" onclick="closeModal('productosModal')">&times;</span>
      <h2>Álbumes de Canserbero</h2>
      <div class="album-container">
          <!-- Álbum Vida -->
          <div class="album">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTktFiovPXXOLNm7hGfVKpmh6Jc7aT7TZp-5g&s" alt="Álbum Vida">
              <h3>Vida (2010)</h3>
              <p>Primer álbum de estudio de Canserbero, lanzado en 2010. Incluye temas como "Pensando en ti" y "Es épico".</p>
          </div>
          <!-- Álbum Muerte -->
          <div class="album">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTZ5wdkvw6ujuUaXLTHrXv9iYUUXFRuWvJDfQ&s" alt="Álbum Muerte">
              <h3>Muerte (2012)</h3>
              <p>Segundo álbum de estudio, lanzado en 2012. Destacan canciones como "C'est la mort" y "Maquiavélico".</p>
          </div>
          <!-- Álbum Apa y Can -->
          <div class="album">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTuBlbLBzyoCPwGiDLD1-IaLswaYYz1CC5B_g&s" alt="Álbum Apa y Can">
              <h3>Apa y Can (2013)</h3>
              <p>Colaboración con el rapero Apache, lanzada en 2013. Incluye tracks como "Ready" y "Stop".</p>
          </div>
          <!-- Álbum Give Me 5 -->
          <div class="album">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQyXCGS0_Sl75raGHGaNOqjEr7d6rnkHntVSw&s" alt="Álbum Give Me 5">
              <h3>Give Me 5 (2016)</h3>
              <p>Último álbum de estudio, publicado en 2016. Contiene canciones como "La vida" y "Es épico".</p>
          </div>
      </div>
  </div>
</div>

<!-- Ventana Modal para Información -->
<div id="informacionModal" class="modal">
    <div class="modal-content">
        <span class="close" onclick="closeModal('informacionModal')">&times;</span>
        <h2>INFORMACION</h2>
        <p>Tirone José González Orama (Caracas, 11 de marzo de 1988-Maracay, 19 de enero de 2015) conocido artísticamente como Canserbero, fue un rapero...</p>
    </div>
</div>

<!-- Script para abrir y cerrar las ventanas modales -->
<script>
    function openModal(modalId) {
        document.getElementById(modalId).style.display = "block";
    }

    function closeModal(modalId) {
        document.getElementById(modalId).style.display = "none";
    }

    window.onclick = function(event) {
        var modals = document.getElementsByClassName("modal");
        for (var i = 0; i < modals.length; i++) {
            if (event.target == modals[i]) {
                modals[i].style.display = "none";
            }
        }
    }

    // Función para agregar una nueva opinión
    function addOpinion() {
        // Obtener los valores del formulario
        const author = document.getElementById('author').value;
        const opinionText = document.getElementById('opinionText').value;

        if (author && opinionText) {
            // Crear una nueva opinión
            const opinion = {
                author: author,
                text: opinionText,
                date: new Date().toLocaleString(),
                votes: 0
            };

            // Agregar la opinión a la lista
            const opinionsList = document.getElementById('opinionsList');
            const opinionDiv = document.createElement('div');
            opinionDiv.classList.add('opinion');
            opinionDiv.innerHTML = `
                <p class="author">${opinion.author}</p>
                <p class="date">${opinion.date}</p>
                <p>${opinion.text}</p>
                <div class="votes">
                    <button class="vote-button" onclick="voteOpinion(this, 'up')">👍</button>
                    <button class="vote-button" onclick="voteOpinion(this, 'down')">👎</button>
                    <span class="vote-count">${opinion.votes} votos</span>
                </div>
            `;

            opinionsList.appendChild(opinionDiv);

            // Limpiar los campos del formulario
            document.getElementById('author').value = '';
            document.getElementById('opinionText').value = '';
        } else {
            alert("Por favor, completa todos los campos.");
        }
    }

    // Función para votar una opinión
    function voteOpinion(button, type) {
        const opinionDiv = button.closest('.opinion');
        const voteCountSpan = opinionDiv.querySelector('.vote-count');
        let currentVotes = parseInt(voteCountSpan.innerText.split(' ')[0]);

        if (type === 'up') {
            currentVotes++;
        } else if (type === 'down') {
            currentVotes--;
        }

        // Actualizar el contador de votos
        voteCountSpan.innerText = `${currentVotes} votos`;
    }
</script>

</body>
</html>
<!-- Sección de Bienvenida -->
<div class="welcome-section">
  <h2>¡Bienvenido a la página en donde queremos a Canserbero!</h2>
  <p>En este espacio podrás conocer más sobre el legado de Canserbero, escuchar sus álbumes y compartir tus opiniones sobre su música. Canserbero fue uno de los artistas más influyentes del rap latinoamericano, y su música sigue viva en nuestros corazones, le debo demasiado respeto y mas por su capacidad de traernos todas esas emociones en canciones, un ser que en vida hizo cosas maravillosas, influenciando a las personas a no solo tener un cambi si no tratar de ser mejores, porque como alguna vez dijo "antes de cambiar al mundo primero cambiate a ti.".</p>

  <div class="image-gallery">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsOm0_IdmLQ5ZQhcylnn8cOUAMccCb1nhY-A&s" alt="Canserbero en concierto" class="image-1">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQDl6fVQorUmK544YtVH_nO8Biz7tX6JpzVLw&s" alt="Canserbero en estudio" class="image-2">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS5uQ1OZvExGYuW3KpskbG-wSsrJK2m7rpLvg&s" alt="Canserbero artwork" class="image-3">
  </div>
</div>

<!-- Estilos para la sección de bienvenida -->
<style>
  .welcome-section {
      padding: 50px;
      background-color: #f0f0f0;
      text-align: center;
  }

  .welcome-section h2 {
      font-size: 2.5rem;
      margin-bottom: 20px;
      color: #333;
  }

  .welcome-section p {
      font-size: 1.2rem;
      color: #555;
      margin-bottom: 30px;
  }

  .image-gallery {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
  }

  .image-gallery img {
      width: 300px;
      height: auto;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      transition: 0.5s ease;
  }

  /* Animación para la primera imagen */
  .image-1:hover {
      transform: rotate(10deg);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
  }

  /* Animación para la segunda imagen */
  .image-2:hover {
      transform: scale(1.1);
      opacity: 0.8;
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
  }

  /* Animación para la tercera imagen */
  .image-3:hover {
      transform: translateY(-10px);
      opacity: 1;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
  }

  .image-gallery img:hover {
      cursor: pointer;
  }
</style>
<!-- Sección de Video -->
<div class="video-section">
  <header>
  <h2>Disfruta de su música</h2>
  <p>A continuación, te dejamos uno de los videos más populares de Canserbero. ¡Que lo disfrutes!</p>
  
  <div class="video-container">
      <!-- Aquí agregamos un video de YouTube como ejemplo -->
      <iframe width="560" height="315" src="https://www.youtube.com/embed/KSW_h8C3OHQ?si=u_E568OCO-5fvBHn" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
</div>
</header>
<br>


<style>
  nav ul {
      display: flex;
      list-style: none;
      padding: 0;
      justify-content: center;
      background-color: #111;
  }

  nav ul li {
      margin: 0 20px;
  }

  nav ul li a {
      color: #fff;
      text-decoration: none;
      font-size: 1.2rem;
  }

  nav ul li a:hover {
      color: #f39c12;
  }
</style>
<div id="galeria" class="gallery-section">
  <title>Galeria de Imagenes</title>
  <h2>aca tenemos nuestra galeria de imagenes sobre canserbero</h2>
  <div class="gallery">
      <img src="img/descarga.jpeg" alt="Imagen 1">
      <img src="img/img can web 2.jpeg" alt="Imagen 2">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCBYRBRqq9JYgXLBQoisek1-a7Km5tYJgWWA&s" alt="Imagen 3">
      <!-- Agregar más imágenes -->
  </div>
</div>

<style>
  .gallery-section {
      text-align: center;
      padding: 50px;
      background-color: #333;
      color: #fff;
  }

  .gallery img {
      width: 30%;
      margin: 10px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }

  .gallery img:hover {
      transform: scale(1.1);
      transition: transform 0.3s ease-in-out;
  }
</style>
<div id="biografia" class="biography-section">
  <h2>Biografía</h2>
  <p>Canserbero, quien también se hace llamar jocosamente “Ser Vero”, en ocasiones se presenta como “Índigo”, “Knpesino” y “El Chamo González”. 

    Tyrone es un popular cantautor, músico de Hip Hop y activista a favor de cambios positivos, nacido en Caracas, Venezuela, el 11 de marzo de 1988. Cuando cumplió 4 años se mudó a Maracay. A sus 9 falleció su madre y se crió en compañía de su papá.
    
    A los 11 comienza a improvisar letras sobre bases de Reggaetón y Hip Hop, ya como Canserbero. Tres años más tarde recibe la noticia de la muerte de su hermano mayor por parte de padre (víctima de la violencia). Durante los siguientes años Canserbero comienza a inclinarse hacia corrientes más oscuras en la música como el Hard Rock y el Hip Hop de los 90s y a su vez se aprecia una modificación hacia el sentido y el porqué de su música, observando un giro en sus ideales personales que lo llevan a componer de manera mucho más seria y profunda. 
    
    Canserbero conoce a Manuel Galvis (Blackamikace) y al ya beatmaker y productor Leonardo Díaz (Afromack), quienes vivían cerca de su residencia ubicada en un vecindario llamado Ánimas 1 de La Pica en Palo Negro. Canserbero y Blackamikace deciden formar una agrupación de Hip Hop y debido a su poca experiencia acuden a la ayuda de Afromack, conformando así un proyecto titulado “Códigos de Barrio”, donde compusieron múltiples temas, aunque sólo se grabaron unos tres o cuatro, motivado también a la escasez de recursos y a la corta edad de ambos. 
    
    Era ya 2003 cuando “Códigos de Barrio” se foguea en el creciente movimiento regional de Hip Hop, cuyas influencias eran motivadas por bandas locales establecidas como Comando 57 (Sombra & Dj Afromack) y Supremacy Hip Hop Clan (Lil Supa y Daniggaz).
    
    En 2004 conoce a Lil Supa entre pasillos de la universidad donde ambos cursaban la carrera de Informática Técnica; Lil Supa lo invitaría al estudio de Luis Muñoz (Gbeck), el que más tarde sería conocido como estudios “El Techo”, y es allí donde Canserbero ingresa como invitado a una producción con el nombre de “Basyco, Base y Contenido” la cual trataba de un compilado de artistas de Hip Hop emergentes en esta cultura (Gbeck, La Zaga, Kpú, Ray, Lil Supa, Gary, Daniggaz, Wake5, Nico) en evolución en Venezuela. Más tarde esta producción se transformaría en una banda, pionera de un Rap en Venezuela cuyas letras rechazan la violencia. 
    
    Después de cuatro años aprendiendo con Basyco a través de las múltiples presentaciones y temas grabados en El Techo -que a su vez se distribuían por medio del Internet- Canserbero y Lil Supa deciden producir un álbum juntos, llamado “Índigos, Can+Zoo” (2008), el cual provocó un impacto importante en la movida nacional y latinoamericana del Rap. Demostrando el buen momento que ambos artistas atravesaban realizaron una gira nacional que a pesar de los pocos recursos fue recibida con ansias por los escuchas de este género. El álbum se agotó en muy poco tiempo.
    
    Luego, en 2009, Canserbero decide compilar los temas previamente distribuidos por Internet además de un sencillo principal, elaborando así un “mixtape” titulado “Nuestra Doctrina No Es Un Dogma, Es Una Guía Para la Acción”, cuya distribución fue gratuita y exclusivamente vía Internet. 
    
    En 2010 edita “Vida”, producido en su totalidad por KPU (Leandro Añez), grabado y editado en Caracas por KPU y Canserbero. Dos años después sale “Muerte”, en contraposición del trabajo anterior.
    
    En 2013 Canserbero se une a Apache para editar el álbum “Apa y Can”.
    
    El 3 de diciembre de 2014 Tyrone visita Argentina en gira de promoción y da una entrevista en CM.
    
    El 20 de enero de 2015 Canserbero protagoniza un confuso episodio. Perdiendo la vida Tyrone y su amigo y colega Carlos Molnar, bajista de la banda reggae Zion TPL. En la madrugada, según dieron a conocer los medios gráficos venezolanos, Tyrone llamó a la puerta de la habitación de Carlos y cuando este respondió, comenzó a golpearlo y lo apuñaló varias veces, provocando su muerte. Luego, Canserbero se suicidó lanzándose por la ventana del departamento del décimo piso del edificio Camino Real en Maracay, Venezuela, donde Molnar vivía con su mujer y sus hijos.
    
    El 26 de diciembre de 2023, a menos de 1 mes de cumplirse 9 años de la muerte de Canserbero, Natalia Améstica, (esposa de Carlos Molnar y ex manager de Canserbero confesó ser la autora del crimen de ambos músicos)..</p>
  <!-- Agregar más contenido de la biografía -->
</div>

<style>
  .biography-section {
      padding: 50px;
      background-color: #222;
      color: #fff;
      text-align: justify;
  }

  .biography-section h2 {
      font-size: 2.5rem;
      margin-bottom: 20px;
  }

  .biography-section p {
      font-size: 1.2rem;
  }
</style>
<div id="contacto" class="contact-section">
  <h2>Contacto</h2>
  <form action="#" method="post">
      <label for="nombre">Nombre:</label>
      <input type="text" id="nombre" name="nombre" required>

      <label for="email">Correo Electrónico:</label>
      <input type="email" id="email" name="email" required>

      <label for="mensaje">Mensaje:</label>
      <textarea id="mensaje" name="mensaje" required></textarea>

      <button type="submit">Enviar</button>
  </form>
</div>

<style>
  .contact-section {
      padding: 50px;
      background-color: #111;
      color: #fff;
  }

  .contact-section h2 {
      font-size: 2.5rem;
      margin-bottom: 20px;
  }

  .contact-section form {
      display: flex;
      flex-direction: column;
      max-width: 600px;
      margin: 0 auto;
  }

  .contact-section input, .contact-section textarea {
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #fff;
      background-color: #333;
      color: #fff;
      border-radius: 5px;
  }

  .contact-section button {
      padding: 10px;
      background-color: #f39c12;
      border: none;
      color: #fff;
      font-size: 1.1rem;
      border-radius: 5px;
      cursor: pointer;
  }

  .contact-section button:hover {
      background-color: #e67e22;
  }
</style>
<div id="musica" class="music-section">
  <h2>Discografía</h2>
  <ul>
      <li>Disco 1 - <a href="https://youtu.be/8cKvvmPwgP4?si=cggn1kGuUZkA-dba">Escuchar</a></li>
      <li>Disco 2 - <a href="https://youtu.be/11IWuxAMEn8?si=66M-sX3gVsKqQcm0">Escuchar</a></li>
      <li>Disco 3 - <a href="https://youtu.be/VDBN0xHD1Uc?si=xRZeGD3jI0ufm2aC">Escuchar</a></li>
      <li>Disco 4 - <a href="https://youtu.be/iUN3XfoGV0A?si=sc0BM5Qg5lkIV55C">Escuchar</a></li>
      <li>Disco 5 - <a href="https://youtu.be/-ZrsFSco8X0?si=1NRB9gP_17QuVRLC">Escuchar</a></li>
      <li>Disco 6 - <a href="https://youtu.be/dGzpsBSJZow?si=uJWYyKatnFnUHfWw">Escuchar</a></li>
      <li>Disco 7 - <a href="https://youtu.be/kSk0kbHMGxw?si=oO6qalTLbYOcEhI0">Escuchar</a></li>
      <li>Disco 8 - <a href="https://youtu.be/kSk0kbHMGxw?si=oO6qalTLbYOcEhI0">Escuchar</a></li>
      <li>Disco 9 - <a href="https://youtu.be/DxkGu2v1ROM?si=1SjbewUdpwGUD3UL">Escuchar</a></li>
      <li>Disco 10 - <a href="https://youtu.be/x0lHTtbWs_c?si=siGfSBElp18XhHdc">Escuchar</a></li>
  </ul>
</div>

<style>
  .music-section {
      padding: 50px;
      background-color: #333;
      color: #fff;
      text-align: center;
  }

  .music-section h2 {
      font-size: 2.5rem;
      margin-bottom: 20px;
  }

  .music-section ul {
      list-style: none;
      padding: 0;
  }

  .music-section li {
      margin: 10px 0;
      font-size: 1.2rem;
  }

  .music-section a {
      color: #f39c12;
      text-decoration: none;
  }

  .music-section a:hover {
      text-decoration: underline;
  }
</style>













]()
