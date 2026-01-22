# ChurnInsight — Predicción Inteligente de Cancelación de Clientes (MVP)

ChurnInsight es un proyecto desarrollado durante un hackathon cuyo objetivo es predecir de forma anticipada si un cliente es propenso a cancelar un servicio (churn), permitiendo que las empresas actúen de manera preventiva para mejorar la retención y reducir pérdidas económicas.

La predicción se expone mediante una API REST, permitiendo su integración con sistemas de marketing, soporte y analítica.



## Sector de Aplicación

Esta solución es útil para empresas con clientes recurrentes, como:

- Telecomunicaciones  
- Fintech y banca digital  
- Streaming  
- E-commerce  
- Software como Servicio (SaaS)

En estos sectores, la retención de clientes es clave para la sostenibilidad del negocio.



## Problema que Resolvemos

Las empresas suelen detectar el churn cuando ya ocurrió.  
Esto impide aplicar acciones de retención oportunas y obliga a invertir más en adquisición de nuevos clientes.

Además, las campañas suelen ser generales y no priorizan clientes con mayor riesgo.



## Nuestra Solución

ChurnInsight permite:

- Analizar datos históricos de clientes  
- Calcular la probabilidad de cancelación  
- Exponer esa predicción mediante una API  
- Permitir acciones preventivas basadas en riesgo

La respuesta del sistema incluye:

- Una clasificación binaria: **"Va a cancelar/ Va a continuar"**
- Una probabilidad asociada para priorización operativa



## Evaluación del Modelo

El modelo fue evaluado utilizando métricas de clasificación estándar:

- Accuracy  
- Precision  
- Recall  
- F1-score  

Dado el contexto de negocio, se priorizó el **Recall**, buscando identificar la mayor cantidad posible de clientes en riesgo de churn, incluso aceptando algunos falsos positivos.

Para el MVP se priorizó un modelo **interpretable (Regresión Logística)**, favoreciendo:

- Explicabilidad
- Estabilidad
- Facilidad de integración.

Los resultados detallados del entrenamiento y validación se documentan en el repositorio de Data Science.



## Arquitectura del Sistema

El sistema está diseñado con una arquitectura desacoplada entre Backend y Data Science, comunicados mediante API.

### Flujo de Predicción
```text
Cliente / Frontend
        ↓
API REST (Spring Boot - Java)
        ↓
Microservicio Data Science (FastAPI - Python)
        ↓
Pipeline de Preprocesamiento + Modelo ML
        ↓
Predicción + Probabilidad
        ↓
Respuesta JSON al cliente
```


Esta arquitectura permite escalar y evolucionar el modelo sin afectar la API.

### Responsabilidades

**Backend**
- Exposición de endpoints REST  
- Validación de solicitudes  
- Orquestación de la predicción  
- Manejo de errores y respuestas  

**Data Science**
- Preprocesamiento de variables  
- Entrenamiento y evalución del modelo
- Serialización del pipeline   
- Validación de dominios y consistencia con el contrato.


## Contrato de Integración (API) - v3(estable)

### Request (ejemplo)

```json
{
  "geography": "Spain",
  "gender": "Male",
  "age": 42,
  "creditScore": 650,
  "balance": 1200.5,
  "estimatedSalary": 45000,
  "tenure": 6,
  "numOfProducts": 2,
  "satisfactionScore": 2,
  "isActiveMember": true,
  "hasCrCard": true,
  "complain": false
}


Response
{
  "forecast": "Va a cancelar",
  "probability": 0.81
}

```
La validación de rangos y dominios de datos se realiza tanto en backend como en el pipeline de Data Science para evitar inferencias fuera del dominio del modelo.

## Pruebas con Postman
El proyecto incluye una colección de Postman para facilitar la validación de la API.

Ubicación:
/postman/ChurnInsight.postman_collection.json

Permite:
- Ejecutar peticiones de prueba al endpoint /predict

- Validar formato de request y response

- Simular distintos escenarios de clientes



## Casos de Uso

- Campañas de retención dirigidas

- Priorización de clientes en soporte

- Segmentación de clientes por riesgo

- Evaluación del impacto de acciones comerciales





## Demo del Sistema

Durante la presentación se demuestra:

- Envío de request desde Postman

- Respuesta con predicción y probabilidad

- Integración activa entre Backend y Data Science


- El objetivo del MVP es validar la viabilidad técnica y de producto de la solución.




## Repositorios del Proyecto

El proyecto se organiza en los siguientes repositorios:

- churn-insight → documentación general y orquestación

- backend → API REST en Java

- data-science → notebooks, pipeline y modelo ML


Cada repositorio contiene documentación técnica específica.




## Equipo y Forma de Trabajo

El proyecto fue desarrollado de forma colaborativa por integrantes de Data Science y Backend.

Aunque algunos commits fueron centralizados por motivos de integración, el trabajo se realizó mediante:

- Reuniones de alineación

- Notebooks compartidos

- Definición conjunta del contrato

- Revisión cruzada de decisiones técnicas


El enfoque fue priorizar un MVP completamente funcional e integrado.

## Integrantes
Data Science
- Nicolás Ruiz – LinkedIn
- Claudia Delgado – LinkedIn
- Felipe Octavio Rebolledo Robert – LinkedIn

Backend
- Anghelo Flores – LinkedIn
- Andrea Cecilia Lopez – LinkedIn
- Ashley
- Luis Fernando Jaramillo – .com
- Enrique Castillo – LinkedIn





## Alcance del MVP

- Dataset reducido

- Modelo no está optimizado para producción

- Sin monitoreo continuo


El objetivo principal es validar la integración técnica y el flujo completo de predicción, dejando optimizaciones para iteraciones futuras.




## Roadmap

- Feature engineering adicional

- Explicabilidad del modelo (SHAP)

- Persistencia de predicciones

- Predicción por lotes (batch)

- Dashboard de visualización





## Licencia

Proyecto con fines educativos y demostrativos para hackathon.
