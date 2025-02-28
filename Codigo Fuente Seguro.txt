// Definimos los valores base
var baseSeguro = 2000;

// Porcentajes de recargo según edad
var recargoJoven = 0.1; // 10%
var recargoAdulto = 0.2; // 20%
var recargoMayor = 0.3; // 30%

var extraParejaJoven = 0.1;
var extraParejaAdulta = 0.2;
var extraParejaMayor = 0.3;

var extraPorHijo = 0.2;

// Variables de acumulación
var totalExtra = 0;

// Solicitud de datos al usuario
var usuario = prompt("¡Hola! ¿Cuál es tu nombre?");
var edadUsuario = parseInt(prompt("¿Cuántos años tienes? Ingresa solo números."));

// Verificar si es mayor de edad
if (edadUsuario < 18) {
  alert("Lo sentimos, debes tener al menos 18 años para cotizar el seguro.");
} else {
  var tienePareja = prompt("¿Tienes pareja? (Sí/No)").toUpperCase();
  var edadPareja = 0;
  
  if (tienePareja === "SÍ") {
    edadPareja = parseInt(prompt("¿Cuántos años tiene tu pareja?"));
  }
  
  var tieneHijos = prompt("¿Tienes hijos? (Sí/No)").toUpperCase();
  var cantidadHijos = (tieneHijos === "SÍ") ? parseInt(prompt("¿Cuántos hijos tienes?")) : 0;
  
  // Aplicar recargo por edad del usuario
  if (edadUsuario < 25) {
    totalExtra += baseSeguro * recargoJoven;
  } else if (edadUsuario < 50) {
    totalExtra += baseSeguro * recargoAdulto;
  } else {
    totalExtra += baseSeguro * recargoMayor;
  }
  
  // Aplicar recargo por edad de la pareja
  if (tienePareja === "SÍ") {
    if (edadPareja < 25) {
      totalExtra += baseSeguro * extraParejaJoven;
    } else if (edadPareja < 50) {
      totalExtra += baseSeguro * extraParejaAdulta;
    } else {
      totalExtra += baseSeguro * extraParejaMayor;
    }
  }
  
  // Aplicar recargo por hijos
  totalExtra += cantidadHijos * (baseSeguro * extraPorHijo);
  
  // Calcular precio final
  var totalPagar = baseSeguro + totalExtra;
  
  // Mostrar resultados
  alert("Hola, " + usuario + "!");
  alert("El recargo total es: Q." + totalExtra);
  alert("El precio final de tu seguro es: Q." + totalPagar);
}