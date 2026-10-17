# chatbot.html
Educativo
<!DOCTYPE html> 
<html lang="es"> 
<head> 
  <meta charset="UTF-8"> 
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
  <title>Chatbot Educativo</title> 
  <style> 
    body { 
      font-family: Arial, sans-serif; 
      background-color: #9bdcbc4e; 
      display: flex; 
      justify-content: center; 
      align-items: center; 
      height: 100vh; 
      margin: 0; 
    } 
    .chat-container { 
      width: 100%; 
      max-width: 400px; 
      background: #a0ead4; 
      border-radius: 12px; 
      box-shadow: 0 4px 8px rgba(0,0,0,0.1); 
      display: flex; 
      flex-direction: column; 
      overflow: hidden; 
    } 
    .messages { 
      flex: 1; 
      padding: 15px; 
      overflow-y: auto; 
    } 
    .message { 
      margin: 8px 0; 
      padding: 10px; 
      border-radius: 10px; 
      max-width: 80%; 
    } 
    .user { 
      background-color: #9bd9c8b8;  
      align-self: flex-end; 
    } 
    .bot { 
      background-color: #e9ecef; 
      align-self: flex-start; 
    } 
    .input-area { 
display: flex; 
border-top: 1px solid #ccc; 
} 
.input-area input { 
flex: 1; 
padding: 12px; 
border: none; 
outline: none; 
font-size: 14px; 
} 
.input-area button { 
padding: 12px; 
background: #007bff; 
color: white; 
border: none; 
cursor: pointer; 
} 
.input-area button:hover { 
background: #0056b3; 
} 
</style> 
</head> 
<body> 
<div class="chat-container" role="region" aria-label="Chat con el bot educativo"> 
<div class="messages" id="messages"></div> 
<div class="input-area"> 
<input type="text" id="userInput" aria-label="Escribe tu pregunta" 
placeholder="Escribe tu pregunta..." /> 
<button onclick="sendMessage()">Enviar</button> 
</div> 
</div> 
<script> 

const messages = document.getElementById("messages"); 
function addMessage(text, sender) { 
const div = document.createElement("div"); 
div.classList.add("message", sender); 
div.textContent = text; 
messages.appendChild(div); 
messages.scrollTop = messages.scrollHeight; 
} 
function botResponse(input) { 
const pregunta = input.toLowerCase(); 
if (pregunta.includes("hola")) { 
return "Contratar a el Maestro de construcción."; 
}
if (pregunta.includes("pegado de adobes")) {
    return "El Maestro cobra 15 Dolares el día"
}
 else if (pregunta.includes("revoque")) { 
return "El Maestro cobra 10 Dolares el día"; 
} else if (pregunta.includes("pintura")) { 
return "El Maestro cobra 5 Dolares el día"; 
}
else if (pregunta.includes("contratar")) { 
return "Perfecto!, tenemos disponible el proximo mes. "; 
}
else if (pregunta.includes("salir")) { 
return "Gracias por conversar conmigo. ¡Éxitos en tu proyecto! "; 
} else { 
return "Lo siento, aún no tengo respuesta para esa pregunta."; 
} 
} 
function sendMessage() { 
const input = document.getElementById("userInput"); 
const text = input.value.trim(); 
if (!text) return; 
addMessage(text, "user"); 
input.value = ""; 
const respuesta = botResponse(text); 
setTimeout(() => addMessage(respuesta, "bot"), 500); // pequeña pausa para simular procesamiento 
} 
// Permite enviar con Enter 
document.getElementById("userInput").addEventListener("keypress", (e) => { 
if (e.key === "Enter") sendMessage(); 
}); 
</script> 
</body> 
</html> 
