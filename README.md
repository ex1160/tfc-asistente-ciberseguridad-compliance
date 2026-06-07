# **Problema y usuario**

MIDTECH necesita analizar políticas de seguridad y detectar incumplimientos normativos automáticamente. Con ese objetivo, se realizará un asistente de ciberseguridad y compliance. El usuario objetivo es el trabajador encargado de la cumplimentación de la normativa y el posible auditor.
Tecnologías elegidas

**LLM**
_Gemini_: Por su facilidad de uso para usuarios principiantes y su razonamiento avanzado. Además la suscripción de Google One para Google Drive incluye el plan de Gemini.

**Orquestación**
_n8n_: Mejor integración con Gemini que Make, muy visual, más común en entornos profesionales.

**Gestor documental**
_Google Drive_: Experiencia previa con las herramientas de Google.

# **Flujo de las 4 capacidades**

**Análisis de políticas**
Entrada: el usuario envía el mensaje “Analiza la política de MIDTECH” junto al documento.
Proceso: n8n analiza el documento, lo divide en fragmentos, busca en el RAG los fragmentos más relevantes y los envía al LLM con el prompt de sistema. 
Salida: Informe de análisis con tres secciones diferenciadas (áreas cubiertas, nivel de cobertura y áreas ausentes).

**Detección de riesgos**
Entrada: el usuario envía el mensaje “realiza un gap analysis de riesgos e incumplimientos” junto al documento de política de MIDTECH.
Proceso: n8n recupera los documentos desde Google Drive, lo divide en fragmentos, busca en el RAG los fragmentos más relevantes y los envía al LLM con el prompt de sistema. 
Salida: Gap analysis con una entrada por cada incumplimiento.

**Respuesta a preguntas de auditoría**
Entrada: el usuario envía preguntas de auditoría al chatbot junto al documento de política de MIDTECH.
Proceso: n8n recupera los documentos desde Google Drive, lo divide en fragmentos, busca en el RAG los fragmentos más relevantes y los envía al LLM con el prompt de sistema. 
Salida: Respuesta citando la política vs la normativa.

**Propuestas de mejora**
Entrada: el usuario envía el mensaje “realiza una lista de propuestas de mejora” junto al documento de política de MIDTECH.
Proceso: n8n recupera los documentos desde Google Drive, lo divide en fragmentos, busca en el RAG los fragmentos más relevantes y los envía al LLM con el prompt de sistema.  
Salida: Lista ordenada por prioridad.

# **Diagrama**

```text
  Usuario
   │
   ▼
Chat n8n
   │
   ▼
Workflow de consulta
   │
   ├── RGPD.pdf
   ├── ENS.pdf
   └── ISO27001.pdf
         │
         ▼
 Extracción de texto
         │
         ▼
 OpenAI Chat Model
         │
         ▼
 Respuesta al usuario
```
