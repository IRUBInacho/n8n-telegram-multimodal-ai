n8n Telegram Multimodal AI Agent
Este repositorio contiene un flujo de trabajo avanzado de n8n que implementa un asistente inteligente en Telegram capaz de procesar texto y voz de manera fluida. La arquitectura utiliza un sistema de buffering con Redis para gestionar ráfagas de mensajes y optimizar las llamadas a los modelos de lenguaje (LLM).

🚀 Características Principales
Entrada Multimodal: El sistema detecta automáticamente si el mensaje es de texto o una nota de voz.

Transcripción Inteligente: Utiliza models/gemini-3-flash-preview para transcribir mensajes de voz con alta precisión.

Gestión de Estado (Buffering): Implementa una lógica con Redis y nodos de espera (Wait) para acumular mensajes del usuario y procesarlos como una sola consulta, evitando respuestas fragmentadas.

Agente de IA Potente: Configurado con un nodo de AI Agent que utiliza modelos de Groq (gpt-oss-120b) y Google Gemini para razonar y responder.

Formateo de Salida: Incluye un nodo de código JavaScript que limpia y adapta el Markdown (títulos y tablas) al formato visual de Telegram para una mejor experiencia de lectura.

🛠️ Requisitos Técnicos
Para utilizar este flujo, necesitarás las siguientes credenciales y servicios:

n8n: Una instancia activa (Self-hosted o Cloud).

Redis: Una base de datos Redis accesible para el almacenamiento temporal.

Telegram Bot API: Un token de bot obtenido a través de @BotFather.

Google Gemini API: Para la transcripción y el modelo de lenguaje.

Groq API: Para la inferencia ultrarrápida del agente.

📦 Instalación
Crea un nuevo flujo de trabajo en tu instancia de n8n.

Copia el contenido del archivo telegram-multimodal-ai.json de este repositorio.

Pégalo directamente en el lienzo de n8n.

Configura las credenciales correspondientes para cada nodo:

Telegram Trigger & Send Message.

Redis Nodes (Redis2, Redis3, Redis4).

Google Gemini & Groq Chat Models.

🧩 Lógica del Flujo
Recepción: El flujo se activa con un mensaje en Telegram.

Clasificación: Un nodo Switch separa el contenido por tipo (texto/audio).

Normalización: El audio se transcribe y se convierte en texto.

Buffering: El mensaje se guarda en Redis y el sistema espera 2 segundos por si llegan más mensajes del mismo usuario.

Procesamiento: El agente de IA analiza el contexto acumulado y genera una respuesta.

Refinado: Un script de JS formatea la respuesta para que luzca profesional en Telegram.

Envío: El bot responde al usuario final.
