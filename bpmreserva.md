<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BPM SALAS DE ENSAYO</title>
  <style>
    body {
      background-color: black;
      color: white;
      font-family: Arial, sans-serif;
      padding: 20px;
    }

    h1, h3 {
      text-align: center;
    }

    h3 {
      font-size: 24px;
      font-weight: bold;
      color: white;
    }

    form {
      background-color: white;
      color: black;
      padding: 20px;
      border-radius: 10px;
      max-width: 600px;
      margin: auto;
    }

    form input, form select {
      width: 100%;
      box-sizing: border-box;
    }

    iframe {
      display: block;
      margin: 20px auto;
      max-width: 100%;
    }

    .popup {
      display: none;
      position: fixed;
      top: 20%;
      left: 50%;
      transform: translate(-50%, -20%);
      background-color: white;
      color: black;
      padding: 20px;
      border: 2px solid #00ff00;
      z-index: 9999;
      border-radius: 10px;
    }

    .popup img {
      max-width: 100%;
    }

    .popup-close {
      display: block;
      margin-top: 10px;
      text-align: right;
      color: black;
      cursor: pointer;
    }

    button {
      padding: 10px 20px;
      background-color: #00ff00;
      border: none;
      border-radius: 5px;
      color: black;
      font-weight: bold;
      cursor: pointer;
    }

    button:hover {
      background-color: #00cc00;
    }

    a {
      color: #00ff00;
    }
  </style>
</head>
<body>
  <h1>BPM SALAS DE ENSAYO</h1>

  <h3>Sala 1</h3>
  <div style="text-align:center;">
    <iframe width="300" height="500" src="https://www.youtube.com/embed/LrDAVQeh4Y0" frameborder="0" allowfullscreen></iframe>
  </div>

  <h3>Sala 2</h3>
  <div style="text-align:center;">
    <iframe width="300" height="500" src="https://www.youtube.com/embed/S9GIJQ3V134" frameborder="0" allowfullscreen></iframe>
  </div>

  <h3>Sala 3</h3>
  <div style="text-align:center;">
    <iframe width="300" height="500" src="https://www.youtube.com/embed/eUBWOVc9ads" frameborder="0" allowfullscreen></iframe>
  </div>

  <form id="reservaForm" enctype="multipart/form-data">
    <label>Nombre:</label>
    <input type="text" name="nombre" required><br><br>

    <label>Teléfono:</label>
    <input type="number" name="telefono" required><br><br>

    <label>Correo Electrónico:</label>
    <input type="email" name="correo" required><br><br>

    <label>Fecha de Reserva:</label>
    <input type="date" name="fecha" required><br><br>

    <label>Sala:</label>
    <select id="sala" name="sala" required>
      <option value="sala1">Sala 1 - 50 Bs/hora</option>
      <option value="sala2">Sala 2 - 50 Bs/hora</option>
      <option value="sala3">Sala 3 - 70 Bs/hora</option>
    </select><br><br>

    <label>Horario de Inicio:</label>
    <select id="horarioInicio" name="horario_inicio" required></select><br><br>

    <label>Duración (horas):</label>
    <input type="number" id="duracion" name="duracion" min="1" required><br><br>

    <button type="button" onclick="seleccionarInstrumento()">Seleccionar Instrumento Adicional</button><br><br>
    <input type="hidden" id="instrumentoSeleccionado" name="instrumento">

    <p><strong>Precio total: <span id="precioTotal">0.00</span> Bs</strong></p>
    <p><strong>Pago requerido para confirmar (50%): <span id="pagoMitad">0.00</span> Bs</strong></p>

    <button type="button" onclick="mostrarMetodoPago()">Método de Reserva</button><br><br>

    <label>Subir Comprobante de Pago:</label>
    <input type="file" id="comprobante" name="comprobante" accept="image/*" required><br><br>

    <label>
      <input type="checkbox" id="aceptaTerminos" name="acepta_terminos" required>
      Acepto los <a href="#" onclick="mostrarTerminos()">Términos y Condiciones</a>
    </label><br><br>

    <button type="submit">Reservar</button>
  </form>

  <div id="popupMetodoPago" class="popup">
    <h4>Método de Pago (reserva con 50%)</h4>
    <img src="https://i.postimg.cc/nVw7F0kP/IMG-2320.png" alt="Código QR de pago">
    <div class="popup-close" onclick="cerrarPopup()">Cerrar</div>
  </div>

  <div id="terminos" style="display:none; white-space: pre-wrap; background:white; color:black; padding:20px; margin-top:20px; border:1px solid #ccc;">
    <h3>Términos y Condiciones de Uso</h3>
        BPM Salas de Ensayo – Santa Cruz, Bolivia

        <br><br><b>1. Objetivo</b><br>
        Las BPM Salas de Ensayo ofrecen a los músicos y artistas un espacio adecuado para la práctica de sus actividades artísticas en un entorno cómodo y bien equipado.

        <br><br><b>2. Horarios de funcionamiento</b><br>
        Las salas están disponibles de lunes a sábado de 9:00 a 00:00.

        <br><br><b>3. Reservas</b><br>
        Las reservas deben realizarse con al menos una hora de anticipación. No hay restricción de horas de uso, pero se debe realizar la reserva con la debida anticipación.

        <br><br><b>4. Precios</b><br>
        Los precios están indicados en el formulario de reserva y deben ser pagados al momento de confirmar la reserva. Se aceptan pagos por QR o en efectivo en el lugar.

        <br><br><b>5. Cancelaciones y Reprogramaciones</b><br>
        Las cancelaciones deben hacerse con al menos 24 horas de anticipación, y las reprogramaciones pueden hacerse hasta 12 horas antes de la reserva.

        <br><br><b>6. Restricciones</b><br>
        Se prohíbe fumar e ingresar alimentos dentro de las salas. Los usuarios son responsables de mantener la limpieza y el orden dentro del establecimiento.

        <br><br><b>7. Responsabilidad</b><br>
        Los padres o tutores deben supervisar a los menores de edad y serán responsables de su conducta dentro del establecimiento.

        <br><br><b>8. Uso de instrumentos</b><br>
        Las salas están equipadas con batería, amplificadores, micrófonos y consola. Se permite el uso de instrumentos propios, siempre y cuando no interfieran con el equipamiento del lugar.

        <br><br><b>9. Modificaciones</b><br>
        BPM Salas de Ensayo se reserva el derecho de modificar estos términos en cualquier momento.

    </div>

  <script>
    const salaSelect = document.getElementById("sala");
    const horarioInicio = document.getElementById("horarioInicio");
    const duracion = document.getElementById("duracion");
    const precioTotal = document.getElementById("precioTotal");
    const pagoMitad = document.getElementById("pagoMitad");

    for (let hora = 9; hora <= 23.5; hora += 0.5) {
      const h = Math.floor(hora);
      const m = (hora % 1 === 0.5) ? "30" : "00";
      const option = document.createElement("option");
      option.value = `${h}:${m}`;
      option.textContent = `${h}:${m}`;
      horarioInicio.appendChild(option);
    }

    function actualizarPrecios() {
      const dur = parseInt(duracion.value) || 0;
      let precioPorHora = 0;
      if (salaSelect.value === "sala1" || salaSelect.value === "sala2") precioPorHora = 50;
      if (salaSelect.value === "sala3") precioPorHora = 70;
      const total = precioPorHora * dur;
      precioTotal.textContent = total.toFixed(2);
      pagoMitad.textContent = (total / 2).toFixed(2);
    }

    function validarHorarioFinal() {
      const inicio = horarioInicio.value;
      const dur = parseInt(duracion.value) || 0;

      if (!inicio || dur === 0) return;

      const [horaStr, minStr] = inicio.split(":");
      const inicioDecimal = parseInt(horaStr) + (minStr === "30" ? 0.5 : 0);
      const finalDecimal = inicioDecimal + dur;

      if (finalDecimal > 24) {
        alert("La reserva no puede extenderse más allá de las 00:00. Ajusta el horario o duración.");
        duracion.value = "";
        actualizarPrecios();
      }
    }

    salaSelect.addEventListener("change", actualizarPrecios);
    duracion.addEventListener("input", () => {
      actualizarPrecios();
      validarHorarioFinal();
    });
    horarioInicio.addEventListener("change", validarHorarioFinal);

    document.getElementById("reservaForm").addEventListener("submit", function(e) {
      if (!document.getElementById("aceptaTerminos").checked) {
        alert("Debes aceptar los términos y condiciones para continuar.");
        e.preventDefault();
      } else {
        const comprobante = document.getElementById("comprobante").files[0];
        if (!comprobante) {
          alert("Debes subir el comprobante de pago.");
          e.preventDefault();
        } else {
          alert("Reserva enviada. El comprobante se adjuntó correctamente.");
        }
      }
    });

    function mostrarTerminos() {
      document.getElementById("terminos").style.display = 'block';
    }

    function seleccionarInstrumento() {
      const opciones = ["Congas", "Timbales", "Ninguno"];
      const seleccion = prompt("Seleccione un instrumento adicional (Congas, Timbales o Ninguno):");
      if (opciones.includes(seleccion)) {
        document.getElementById("instrumentoSeleccionado").value = seleccion;
        alert("Instrumento seleccionado: " + seleccion);
      } else {
        alert("Selección no válida.");
      }
    }

    function mostrarMetodoPago() {
      document.getElementById("popupMetodoPago").style.display = 'block';
    }

    function cerrarPopup() {
      document.getElementById("popupMetodoPago").style.display = 'none';
    }
  </script>
</body>
</html>
