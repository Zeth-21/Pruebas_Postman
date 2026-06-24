# 👞 Análisis y Pruebas de API REST (E-commerce) - Caso de Estudio: Bruno Ferrini

## Información General
**Objetivo del Proyecto:** Simular las operaciones backend (CRUD) del sistema de gestión de inventario de calzado para la marca Bruno Ferrini utilizando herramientas de prueba de integración.
**Herramienta de Testing:** Postman
**Entorno de Pruebas (API):** [DummyJSON E-commerce API](https://dummyjson.com/docs)

---
## 📚 Documento Monográfico

Añadiendo documento monográfico del trabajo:

👉 **[Ver Trabajo Monográfico (PDF)](https://drive.google.com/file/d/14a8C7rEjUTFv535d8ql3_Lcx08WVjmWL/view?usp=sharing)**

## 1. Introducción y Marco Teórico

Debido a que los sistemas de producción empresariales mantienen sus APIs de escritura privadas por estrictos motivos de seguridad, para este laboratorio se implementó la API pública DummyJSON como entorno de pruebas seguro (*sandbox*). 

Para el desarrollo de esta simulación, se aplicaron los cuatro conceptos fundamentales de arquitectura REST (CRUD):
* **GET (Consultar):** Permite leer recursos del servidor sin modificarlos.
* **POST (Crear):** Envía datos al servidor para registrar un nuevo recurso.
* **PUT (Actualizar):** Modifica o reemplaza los datos de un recurso existente.
* **DELETE (Eliminar):** Retira un recurso específico de la base de datos.

**Códigos de Estado HTTP esperados:**
* **200 OK:** La solicitud se procesó correctamente.
* **201 Created:** El recurso fue creado exitosamente en el servidor.

---

## 2. Desarrollo de Pruebas a Endpoints

A continuación se detalla la documentación de las cuatro pruebas realizadas a los endpoints seleccionados, cubriendo el ciclo de vida de los productos en la tienda.

### Prueba 1: Consultar catálogo de calzado
**URL del endpoint:** `https://dummyjson.com/products/category/mens-shoes`
**Método HTTP utilizado:** GET
**Parámetros enviados:** Ninguno. La categoría viaja en la URL y el Body está configurado en "none".
**Código de estado HTTP recibido:** 200 OK
**Respuesta obtenida:**
```json
{
  "products": [
    {
      "id": 88,
      "title": "Nike Air Jordan 1 Red And Black",
      "price": 149.99,
      "category": "mens-shoes",
      "stock": 7
    }
  ],
  "total": 5,
  "skip": 0,
  "limit": 1
}

### Prueba 2: Registrar un nuevo modelo en la tienda
**URL del endpoint:** `https://dummyjson.com/products/add`
**Método HTTP utilizado:** POST
**Parámetros enviados:** Formato JSON raw en el Body con los datos del nuevo producto Bruno Ferrini.
**Código de estado HTTP recibido:** 201 Created
**Respuesta obtenida:**
```json
{
  "id": 195,
  "title": "Mocasines de Cuero Genuino",
  "description": "Mocasines elegantes Bruno Ferrini 100% cuero para caballero, colección de invierno.",
  "price": 350,
  "category": "mens-shoes",
  "brand": "Bruno Ferrini",
  "stock": 50
}

### Prueba 3: Actualizar precio por campaña de rebajas
**URL del endpoint:** `https://dummyjson.com/products/88`
**Método HTTP utilizado:** PUT
**Parámetros enviados:** Formato JSON raw en el Body actualizando el precio y el stock.
**Código de estado HTTP recibido:** 200 OK
**Respuesta obtenida:**
```json
{
  "id": 88,
  "title": "Nike Air Jordan 1 Red And Black",
  "price": 299,
  "discountPercentage": 15.5,
  "stock": 12,
  "category": "mens-shoes"
}

### Prueba 4: Descatalogar un zapato fuera de temporada
**URL del endpoint:** `https://dummyjson.com/products/88`
**Método HTTP utilizado:** DELETE
**Parámetros enviados:** Ninguno. El ID a eliminar viaja en la URL y el Body está en "none".
**Código de estado HTTP recibido:** 200 OK
**Respuesta obtenida:**
```json
{
  "id": 88,
  "title": "Nike Air Jordan 1 Red And Black",
  "price": 149.99,
  "category": "mens-shoes",
  "isDeleted": true,
  "deletedOn": "2026-06-23T10:15:00.000Z"
}

## Conclusiones

* Mediante el uso de la herramienta Postman, se logró comprobar exitosamente la integración y el correcto funcionamiento de los cuatro métodos HTTP fundamentales aplicados a un entorno de comercio electrónico.
* Se validó la viabilidad y la importancia de utilizar APIs de prueba de acceso público (como DummyJSON) para simular entornos seguros (*sandboxes*). Esto permite modelar operaciones críticas de sistemas empresariales reales, como el control de inventario de Bruno Ferrini, sin comprometer la integridad de bases de datos de producción.
* El análisis técnico permitió comprender a profundidad la estructura de intercambio de datos mediante archivos JSON y las respuestas del servidor. Se verificó que el sistema cumple con los estándares web, retornando códigos de éxito `200 OK` para consultas y modificaciones, y garantizando la confirmación de registros nuevos mediante el código `201 Created`.
