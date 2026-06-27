# Post-Mortem Constructivo: Fricciones en el Embudo de Reservas de TablaYa

*Autor: Sandy Katherine Martin Mendez | Fecha: junio de 2026 | Categoría: Producto Digital, UX/CX, Reservas Online*

> **Nota para el lector:** esta entrada está escrita para ser comprendida tanto por perfiles técnicos (desarrollo, producto) como por perfiles de negocio (operaciones, atención al cliente). Cada término específico de la industria (MTTR, KPI, SLA, conversión) se explica brevemente en su primera aparición.

---

## 1. Contexto

TablaYa es una aplicación de reservas para restaurantes que permite a los usuarios encontrar mesa disponible, reservar en pocos pasos y recibir confirmación inmediata. El producto se dirige principalmente a un perfil que llamamos **Andrés**: 34 años, profesional con agenda variable, que suele decidir dónde cenar con poca anticipación (entre 30 y 90 minutos antes) y que abandona cualquier app que le tome más de un minuto en confirmar una reserva.

El objetivo de este análisis fue auditar el flujo completo de reserva —desde la búsqueda del restaurante hasta la confirmación final— para identificar por qué, a pesar de tener buen tráfico de usuarios nuevos, la tasa de reservas completadas era notablemente inferior a la esperada para este tipo de producto.

### Propósito del ejercicio

- Aplicar un marco de diagnóstico de experiencia de usuario para separar síntomas visuales de causas raíz reales.
- Traducir los hallazgos de negocio en requerimientos técnicos accionables (historias de usuario) para un backlog ágil.
- Practicar la documentación técnica clara para audiencias mixtas, siguiendo la estructura problema–acción–impacto.
- Aplicar y reflexionar sobre el uso de feedback radicalmente sincero durante el proceso de revisión del propio análisis.

---

## 2. Problema

Durante la auditoría del flujo de reserva se identificaron tres capas de fricción que, en conjunto, explicaban la caída de conversión:

| Capa de fricción | Causa raíz diagnosticada | Impacto / consecuencia |
|---|---|---|
| **1. Disponibilidad poco confiable** | Los horarios mostrados como "disponibles" no se sincronizaban en tiempo real con el sistema del restaurante, generando reservas rechazadas tras la confirmación. | Pérdida de confianza inmediata y abandono tras el primer rechazo de reserva. |
| **2. Formulario de reserva extenso** | El flujo solicitaba datos redundantes (nombre, teléfono, correo, preferencias) en pantallas separadas antes de confirmar. | Abandono del proceso (drop-off) entre el paso 2 y el paso 4 del formulario. |
| **3. Confirmación y soporte lentos** | La confirmación final dependía de validación manual por parte del restaurante, sin automatización ni aviso claro de tiempos de espera. | Usuarios reservando en paralelo por otro canal (llamada telefónica) o cancelando por falta de respuesta. |
