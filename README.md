# ChurnInsight — Predicción Inteligente de Cancelación de Clientes

<div align="center">

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5-green)
![Python](https://img.shields.io/badge/Python-3.11-blue)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED)
![License](https://img.shields.io/badge/license-MIT-yellow)

**Plataforma Integral de Predicción y Prevención de Churn de clientes**

</div>

---

## 🎯 Descripción General

**ChurnInsight** es una plataforma completa que combina **Backend Engineering** y **Data Science** para predecir la probabilidad de que un cliente cancele un servicio (churn). La solución permite a las empresas actuar proactivamente, mejorando la retención y reduciendo pérdidas económicas.


### 💼 Sectores de Aplicación
Esta solución es útil para empresas con clientes recurrentes, como:

<table>
<tr>
<td align="center">📱<br><b>Telecom</b></td>
<td align="center">💳<br><b>Fintech</b></td>
<td align="center">💲<br><b>Bank</b></td>
<td align="center">🎬<br><b>Streaming</b></td>
<td align="center">🛒<br><b>E-commerce</b></td>
<td align="center">💪<br><b>Fitness</b></td>
<td align="center">🌐<br><b>SaaS</b></td>
</tr>
</table>

En estos sectores, la retención de clientes es clave para la sostenibilidad del negocio.

### 🎓 Contexto del Proyecto

Desarrollado durante la hackathon **Hackathon ONE Latam II**, diseñado para equipos con conocimientos en:
- ✅ **Backend** con Java (Spring Boot, APIs REST, Base de datos)
- ✅ **Data Science** con Python (Pandas, Scikit-learn, ML supervisado)


---


## 😰 Problema que Resolvemos

Las empresas suelen detectar el churn cuando ya ocurrió, lo que impide aplicar acciones de retención oportunas y obliga a invertir más en adquisición de nuevos clientes.  
Además, muchas campañas son generales y no priorizan a los clientes con mayor riesgo de abandono.


### 💸 Desafíos de Negocio

```
┌──────────────────────────────────────────────────────────────┐
│  Cada cliente perdido representa:                            │
│                                                              │
│  💰 Pérdida de ingresos recurrentes (LTV)                    │
│  📉 Costos de adquisición desperdiciados (CAC)               │
│  😔 Daño a la reputación de marca                            │
│  🔄 Ciclo negativo de deserción                              │
│                                                              │
│  "Retener un cliente es más barato que adquirir uno nuevo"   │
└──────────────────────────────────────────────────────────────┘
```


## ✨ Nuestra Solución

ChurnInsight es una solución que combina Machine Learning con una API REST y Dashboard para predecir de forma anticipada si un cliente es propenso a cancelar un servicio (churn), permitiendo que las empresas actúen de manera preventiva para mejorar la retención y reducir pérdidas económicas.  

El sistema, enfocado en el sector bancario, analiza patrones de comportamiento de clientes y devuelve una predicción con probabilidad numérica, permitiendo que los equipos de marketing, soporte y analítica actúen de forma preventiva y personalizada para retener clientes.

ChurnInsight permite:

- Predicción en tiempo real
- Explicabilidad (top 3 factores de riesgo)
- Persistencia de predicciones
- Procesamiento batch (CSV) para análisis masivos
- Dashboard interactivo con métricas
- API REST documentada y escalable


La respuesta del sistema incluye:

- Una clasificación binaria (**"Va a cancelar"** / **"No va a cancelar"**)  
- Una probabilidad asociada, útil para priorización operativa  
- Top 3 de variables mas relevantes (Con su impacto positivo o negativo)
- Nivel de riesgo (alto, medio, bajo)

### 🎯 Beneficios para el Negocio

<table>
<tr>
<td width="50%">

#### 🔮 **Predicción Proactiva**
- Identifica clientes en riesgo **antes** de cancelar
- Probabilidad numérica precisa (0-100%)
- Actualización en tiempo real
- Segmentación por nivel de riesgo

</td>
<td width="50%">

#### 💡 **Acción Estratégica**
- Prioriza recursos en clientes valiosos
- Personaliza estrategias de retención
- Reduce costos de adquisición

</td>
</tr>
</table>

### 🎬 Ejemplo de Impacto

> **Caso Real - Fintech:**  
> "Detectamos que usuarios con >30 días sin login + balance bajo tenían 82% de churn. Implementamos campaña automática de reactivación → **reducción de 35% en cancelaciones** en 3 meses."



## 🔎 Evaluación del Modelo

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

---

##  🏗️ Arquitectura del Sistema

### Diagrama de Alto Nivel

[imagen (corregir los recursos OCI de abajo si es necesario)]

**☁️ Recursos OCI Utilizados (Free Tier):**
- ✅ **Compute Instances**: 2x VM.Standard.E2.1.Micro (1 OCPU, 1 GB RAM)
- ✅ **Block Volume**: 200 GB (Always Free)
- ✅ **Load Balancer**: 1x Flexible Load Balancer
- ✅ **Autonomous Database**: 2x ATP (20 GB cada uno)
- ✅ **Object Storage**: 20 GB
- ✅ **VCN**: Red virtual privada

---

### 🔄 Flujo de Predicción

```

Cliente / Frontend (Streamlit - Python)
              ↓
Backend API REST (Spring Boot - Java)
              ↓
Microservicio Data Science (FastAPI - Python)
              ↓
Pipeline de Preprocesamiento + Modelo ML
              ↓
Backend API REST (Spring Boot - Java) → Base de datos (PostgreSQL)
              ↓
Cliente / Frontend (Streamlit - Python)

````


Esta arquitectura permite escalar y evolucionar el modelo sin afectar la API.

---

## 📦 Repositorios del Proyecto

### 🏗️ Arquitectura de Repositorios
```
HackathonONELatam-ChurnInsight Organization
│
├─── 📘 churn-insight (este repo)
│    └── Documentación general + Orquestación
│
├─── 📊 frontend
│    └── Dashboard Streamlit
│
├─── ⚙️ backend
│    └── API REST + Backend Services
│
└─── 🤖 data-science
     └── API + ML Models + Notebooks
```

### 1️⃣ 📘 [ChurnInsight Principal](https://github.com/HackathonONELatam-ChurnInsight/churn-insight) (Este Repositorio)

**Propósito:** Documentación general, orquestación y deployment

📁 Contenido del repositorio

```
churn-insight/
├── 📄 README.md                 # Documentación general
├── 📄 docker-compose.yml        # Orquestación completa
│
└── 📂 postman/                  # Colecciones API
    └── ChurnInsight.postman_collection.json

```

### 2️⃣ ⚙️ [Frontend - Streamlit](https://github.com/HackathonONELatam-ChurnInsight/frontend)

**Propósito:** Dashboard de métricas generales, predicción individual y batch


**🔗 Ver Repositorio:** [frontend →](https://github.com/HackathonONELatam-ChurnInsight/frontend)

**📖 Documentación Técnica:** [Frontend README](https://github.com/HackathonONELatam-ChurnInsight/frontend#readme)


### 3️⃣ ⚙️ [Backend API - Java/Spring Boot](https://github.com/HackathonONELatam-ChurnInsight/backend)

**Propósito:** API REST, validación, integración con ML Service


**🔗 Ver Repositorio:** [backend →](https://github.com/HackathonONELatam-ChurnInsight/backend)

**📖 Documentación Técnica:** [Backend README](https://github.com/HackathonONELatam-ChurnInsight/backend#readme)


### 4️⃣ 🤖 [Data Science - Python/ML](https://github.com/HackathonONELatam-ChurnInsight/data-science)

**Propósito:** Modelos ML, pipeline, feature engineering, notebooks de exploración


**🔗 Ver Repositorio:** [data-science →](https://github.com/HackathonONELatam-ChurnInsight/data-science)

**📖 Documentación Técnica:** [Data Science README](https://github.com/HackathonONELatam-ChurnInsight/data-science#readme)


---


## 📜 Contrato de Integración (API)

### Request (ejemplo de predicción individual)

```json
{
  "customerId": "CLI-002",
  "geography": "Spain",
  "gender": "Male",
  "age": 42,
  "creditScore": 650,
  "balance": 14.5,
  "estimatedSalary": 14,
  "tenure": 6,
  "numOfProducts": 3,
  "satisfactionScore": 2,
  "isActiveMember": true,
  "hasCrCard": true,
  "complain": false
}


Response (200 OK)
{
  "forecast": "No va a cancelar",
  "probability": 0.0745,
  "top_features": [
    {
      "name": "IsActiveMember",
      "value": "1",
      "impact": "negativo"
    },
    {
      "name": "Age",
      "value": "42",
      "impact": "positivo"
    },
    {
      "name": "Balance",
      "value": "14.5",
      "impact": "negativo"
    }
  ],
  "riskLevel": "LOW"
}

```

**Variables:**

- **`customerId`**: ID del cliente de la base de datos donde proviene (opcional).
- **`geography`**: País de residencia del cliente.
- **`gender`**: Género del cliente. 
- **`age`**: Edad del cliente en años.
- **`creditScore`**: Puntuación de crédito del cliente, que indica su solvencia financiera.
- **`balance`**: Saldo de la cuenta del cliente.
- **`estimatedSalary`**: Salario estimado del cliente.
- **`tenure`**: Número de años que el cliente ha estado en el banco. 
- **`numOfProducts`**: Número de productos bancarios que el cliente utiliza (por ejemplo, cuentas, tarjetas de crédito).
- **`satisfaction Score`**: Puntuación de satisfacción del cliente.
- **`isActiveMember`**: Indica si el cliente es un miembro activo del banco.
- **`hasCrCard`**: Indica si el cliente posee una tarjeta de crédito.
- **`complain`**: Indica si el cliente ha presentado una queja.


La validación de rangos y dominios de datos se realiza tanto en backend como en el pipeline de Data Science para evitar inferencias fuera del dominio del modelo.


## 📝 Reglas de Dominio y Validación de Datos

Para garantizar que el modelo genere predicciones confiables y evitar inferencias fuera del dominio de entrenamiento, se establecen reglas de validación tanto en Backend como en el pipeline de Data Science.

###  Validación de Dominio (Backend)

Las siguientes reglas aseguran que los datos de entrada cumplan con rangos y valores esperados:

| Variable            | Dominio esperado                       |
|---------------------|-----------------------------------------|
| geography            | Spain, France, Germany                  |
| gender               | Male, Female                           |
| age                  | 18 – 100                                |
| creditScore          | 100 – 1000                              |
| balance              | ≥ 0                                    |
| estimatedSalary      | ≥ 0                                    |
| tenure               | 0 – 20                                 |
| numOfProducts        | 1, 2, 3, 4                             |
| satisfactionScore    | 1, 2, 3, 4, 5                           |
| variables binarias   | true / false                           |

Estas validaciones permiten detectar entradas inválidas antes de ejecutar el modelo y evitar resultados inconsistentes.



###  Clasificación de Variables (Data Science)

Las variables utilizadas por el modelo fueron analizadas durante el EDA y clasificadas según su impacto en la predicción.

#### 🟢 Core — Alta Importancia  
Impactan directamente en el resultado del modelo:

- Age  
- CreditScore  
- Balance  
- Tenure  
- NumOfProducts  
- IsActiveMember  
- SatisfactionScore  
- complain  
- Geography  
- Gender  

Estas variables explican la mayor parte de la variabilidad del riesgo de churn.



#### 🟡 Opcionales — Mejoran performance  
Aportan señal secundaria y pueden mejorar ligeramente el desempeño:

- EstimatedSalary  
- HasCrCard  

No son indispensables para generar predicción.



#### 🔴 Baja relevancia / Descartadas  
No aportan valor predictivo significativo:

- RowNumber  
- CustomerId  
- Surname  

Estas variables fueron excluidas del pipeline para evitar ruido y sobreajuste.



Esta clasificación permite:

- Alinear el contrato de entrada con las variables realmente utilizadas.
- Facilitar la integración con otros equipos.
- Mejorar la trazabilidad y explicabilidad del modelo.




---

## 🚀 Quick Start en 5 Minutos

### Opción 1: Docker Compose (⚡ Recomendado)

```bash
corregir tabla abajo si esta mal
```

**🎉 ¡Listo!** Los servicios están corriendo en:

| Servicio | URL | Descripción |
|----------|-----|-------------|
| 🔹 **API REST** | http://localhost:8080 | Backend principal |
| 🔹 **Swagger UI** | http://localhost:8080/swagger-ui.html | Documentación API |
| 🔹 **ML Service** | http://localhost:8000 | Servicio de ML |
| 🔹 **ML Docs** | http://localhost:8000/docs | Documentación FastAPI |
| 🔹 **PgAdmin** | http://localhost:5050 | Admin BD (admin@churninsight.com/admin123) |

---

### Opción 2: Desarrollo Local

Para la configuración para desarrollo ir a la respectiva documentación.


---

## 🎬 Casos de Uso Reales

### Caso 1: 🔴 Cliente de Alto Riesgo

**Perfil del Cliente:**
```json
{
  "geography": "Spain",
  "gender": "Male",
  "age": 88,
  "creditScore": 650,
  "balance": 14.5,
  "estimatedSalary": 14,
  "tenure": 6,
  "numOfProducts": 3,
  "satisfactionScore": 2,
  "isActiveMember": true,
  "hasCrCard": true,
  "complain": false
}
```

**Predicción del Sistema:**
```json
{
  "forecast": "Va a cancelar",
  "probability": 0.7134,
  "top_features": [
    {
      "name": "Age",
      "value": "88",
      "impact": "positivo"
    },
    {
      "name": "IsActiveMember",
      "value": "1",
      "impact": "negativo"
    },
    {
      "name": "Balance",
      "value": "14.5",
      "impact": "negativo"
    }
  ],
  "riskLevel": "HIGH"
}
```

---

### Caso 2: 🟢 Cliente de Bajo Riesgo

**Perfil del Cliente:**
```json
{
  "geography": "Spain",
  "gender": "Female",
  "age": 25,
  "creditScore": 580,
  "balance": 0.5,
  "estimatedSalary": 140,
  "tenure": 6,
  "numOfProducts": 1,
  "satisfactionScore": 1,
  "isActiveMember": false,
  "hasCrCard": true,
  "complain": false
}
```

**Predicción del Sistema:**
```json
{
  "forecast": "No va a cancelar",
  "probability": 0.0984,
  "top_features": [
    {
      "name": "Age",
      "value": "25",
      "impact": "negativo"
    },
    {
      "name": "Gender",
      "value": "Female",
      "impact": "positivo"
    },
    {
      "name": "Balance",
      "value": "0.5",
      "impact": "negativo"
    }
  ],
  "riskLevel": "LOW"
}
```


## Casos de Uso

- Campañas de retención dirigidas

- Priorización de clientes en soporte

- Segmentación de clientes por riesgo

- Evaluación del impacto de acciones comerciales

---

### Caso 3: 🟡 Cliente de Riesgo Medio

**Perfil del Cliente:**
```json
{
  "geography": "France",
  "gender": "Female",
  "age": 68,
  "creditScore": 650,
  "balance": 14.5,
  "estimatedSalary": 14000,
  "tenure": 6,
  "numOfProducts": 3,
  "satisfactionScore": 2,
  "isActiveMember": true,
  "hasCrCard": true,
  "complain": true
}
```

**Predicción del Sistema:**
```json
{
  "forecast": "Va a cancelar",
  "probability": 0.4791,
  "top_features": [
    {
      "name": "Age",
      "value": "68",
      "impact": "positivo"
    },
    {
      "name": "IsActiveMember",
      "value": "1",
      "impact": "negativo"
    },
    {
      "name": "Gender",
      "value": "Female",
      "impact": "positivo"
    }
  ],
  "riskLevel": "MEDIUM"
}
```

---

## ✅ Pruebas con Postman
El proyecto incluye una colección de Postman y un archivo csv para facilitar la validación de la API.

Ubicación:
```
/postman/ChurnInsight.postman_collection.json
```

Uso: Importa `postman/ChurnInsight.postman_collection.json` en Postman y ejecuta las peticiones o úsalas en el Collection Runner.

Permite:
- Ejecutar peticiones de prueba al endpoint /predict (/predict/with-explanation y /predict/batch)

- Validar formato de request y response

- Simular distintos escenarios de clientes

---

## 🛠️ Stack Tecnológico

### Frontend

| Tecnología | Propósito |
|------------|-----------|
| Python | Lenguaje base |
| Streamlit | Dashboard Framework |

### Backend

| Tecnología | Propósito |
|------------|-----------|
| Java | Lenguaje base |
| Spring Boot | Framework |
| Maven | Build tool |
| PostgreSQL | Base de datos |

### Data Science

| Tecnología | Propósito |
|------------|-----------|
| Python | Lenguaje base |
| FastAPI | Web framework |
| Scikit-learn | ML library |
| Joblib | Model serialization |

### Cloud & DevOps

| Tecnología | Propósito |
|------------|-----------|
| Docker | Contenerización |
| Docker Compose | Orquestación |
| Oracle Cloud (OCI) | Proveedor Cloud |

---

## 📖 Documentación

### 📚 Documentación por Repositorio


| Documento | Ubicación | Descripción |
|-----------|-----------|-------------|
| **Frontend README** | [frontend](https://github.com/HackathonONELatam-ChurnInsight/frontend) | Docs del dashboard |
| **Backend README** | [backend](https://github.com/HackathonONELatam-ChurnInsight/backend) | Docs técnicas backend |
| **Data Science README** | [data-science](https://github.com/HackathonONELatam-ChurnInsight/data-science) | Docs de ML y notebooks |

### 🎓 Recursos

- 📹 [YouTube Video - Demo](https://www.youtube.com/watch?v=HAmE22WBs7g)
- 🎤 [Presentación](https://www.canva.com/design/DAG_Fw94GzU/_gzIzXKX8jdYkN_WI2E0Yg/edit)

---

## 🗺️ Roadmap

### ✅ Fase 1: Funcionalidades Exigidas (Completado)

- [x] API REST con Spring Boot
- [x] ML Service con FastAPI
- [x] Modelo Logistic Regression
- [x] Docker Compose
- [x] Documentación básica
- [x] Tests automatizados
- [x] Documentación API

### ✅ Fase 2: Funcionalidades Opcionales (Completado)

- [x] Explicabilidad del modelo (SHAP)
- [x] Procesamiento batch (CSV)
- [x] Dashboard de visualización
- [x] Persistencia en PostgreSQL
- [x] Endoints de estadísticas y métricas
- [x] Docker Compose completo
- [x] Deploy en Oracle Cloud Infrastucture (Free-Tier)

### 📋 Fase 3: Features Extras

- [ ] Descarga de resultados batch
- [ ] Autorización y autenticación
- [ ] Monitoreo y obersvabilidad


---


## 🤝 Equipo y Forma de Trabajo

El proyecto fue desarrollado de forma colaborativa por integrantes de Data Science y Backend.

Aunque algunos commits fueron centralizados por motivos de integración, el trabajo se realizó mediante:

- Reuniones de alineación

- Notebooks compartidos

- Definición conjunta del contrato

- Revisión cruzada de decisiones técnicas


El enfoque fue priorizar un MVP completamente funcional e integrado y luego pasamos a las funcionalidades opcionales.

El objetivo principal es validar la integración técnica y el flujo completo de predicción, dejando optimizaciones para iteraciones futuras.


### Responsabilidades

### Backend

- Exposición de endpoints REST
- Validar datos de entrada
- Orquestar llamadas al ML Service
- Persistir predicciones
- Proporcionar estadísticas
- Procesar batches 
- Manejo de errores y respuestas  

### Data Science

- Preprocesamiento de variables  
- Ejecución del modelo de Machine Learning  
- Retorno de resultados al backend  
- Validación de dominios y consistencia con el contrato interno.




## 👥 Equipo

### Backend Team
Desarrollado por el Equipo 69 para la Hackathon ONE.

<table>
<tr>
<td align="center" width="150">
<sub><b>Anghelo Flores</b></sub><br />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anghelo-flores-4725451b1/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/evanghel1on)
</td>
<td align="center" width="150">
<sub><b>Andrea Cecilia Lopez</b></sub><br />


[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/andreacecilialopez)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ProfeCeci)
</td>
<td align="center" width="150">
<sub><b>Ashley Villanueva</b></sub><br />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://pe.linkedin.com/in/ashley-zifrikc-dev)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Zifrikc)
</td>
<td align="center" width="150">
<sub><b>Luis Fernando Jaramillo</b></sub><br />

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jaramilloster)
</td>
<td align="center" width="150">
<sub><b>Enrique Castillo</b></sub><br />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joseenriquecastillo/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kikecastillocolombia)
</td>
</tr>
</table>

### Data Science Team

<table>
<tr>
<td align="center" width="150">
<sub><b>Nicolás Ruiz</b></sub><br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/nicolas-ruiz-953323302)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Noirwolf04)
</td>
<td align="center" width="150">
<sub><b>Claudia Delgado</b></sub><br />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/claudiax-delgado)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ClaudiaXDG)
</td>
<td align="center" width="150">
<sub><b>Felipe Rebolledo Robert</b></sub><br />

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/felipe-rebolledo-robert/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/FelipeOctavio87)
</td>
</tr>
</table>







## 📄 Licencia

Proyecto con fines educativos y demostrativos para hackathon.

---

<div align="center">

### 🌟 Si este proyecto te fue útil, ¡dale una estrella! ⭐

**Desarrollado con ❤️ por el Equipo ChurnInsight**

[![Frontend](https://img.shields.io/badge/🔗%20Frontend-Repository-yellow?style=for-the-badge)](https://github.com/HackathonONELatam-ChurnInsight/frontend)
[![Backend](https://img.shields.io/badge/🔗%20Backend-Repository-blue?style=for-the-badge)](https://github.com/HackathonONELatam-ChurnInsight/backend)
[![Data Science](https://img.shields.io/badge/🔗%20Data%20Science-Repository-green?style=for-the-badge)](https://github.com/HackathonONELatam-ChurnInsight/data-science)

</div>
