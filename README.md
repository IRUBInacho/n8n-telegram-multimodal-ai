# 🤖 n8n Telegram Multimodal AI Agent

Flujo de trabajo avanzado en **n8n** que implementa un **asistente inteligente para Telegram**, capaz de procesar **texto y notas de voz** de forma fluida y contextual.

El sistema utiliza **Redis como buffer de mensajes**, permitiendo agrupar múltiples inputs del usuario en una sola consulta y optimizar las llamadas a modelos de lenguaje (LLM).

---

## 🚀 Características

- **Entrada multimodal**: detección automática de texto y audio.
- **Transcripción de voz** con Google Gemini (`gemini-3-flash-preview`).
- **Buffering con Redis** para evitar respuestas fragmentadas.
- **Agente de IA avanzado**:
  - Groq (`gpt-oss-120b`) para razonamiento ultrarrápido.
  - Google Gemini como modelo complementario.
- **Formateo optimizado para Telegram** (Markdown adaptado con JavaScript).

---

## 🧩 Extensibilidad (Tools & Memory)

El agente de IA está diseñado para ser **totalmente extensible**, según las necesidades del cliente:

- **Tools personalizadas**:
  - APIs externas
  - Bases de datos
  - Lógica de negocio o validaciones
- **Memoria configurable**:
  - Memoria corta (Redis / contexto temporal)
  - Memoria persistente o semántica (vector stores)
- Permite escalar desde un bot simple hasta un **asistente empresarial**.

---

## 🛠️ Requisitos

- **n8n** (Self-hosted o Cloud)
- **Redis**
- **Telegram Bot API**
- **Google Gemini API**
- **Groq API**

---

## 📦 Instalación

1. Crea un nuevo workflow en **n8n**.
2. Copia el contenido de `telegram-multimodal-ai.json`.
3. Pégalo en el lienzo de n8n.
4. Configura las credenciales de:
   - Telegram
   - Redis
   - Google Gemini
   - Groq

---

## 🔄 Flujo de Trabajo

1. Recibe mensaje desde Telegram  
2. Clasifica texto o audio  
3. Transcribe si es voz  
4. Guarda y agrupa mensajes en Redis  
5. Procesa contexto con el agente de IA  
6. Ajusta formato para Telegram  
7. Responde al usuario  

---

## 📌 Casos de Uso

- Chatbots avanzados en Telegram, WhatsApp, Facebook, etc.
- Asistentes de voz, texto, archivos e imagenes.
- Bots con contexto real y memoria.
- Optimización de costos LLM mediante batching.
