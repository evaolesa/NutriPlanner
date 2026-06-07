# Prompt: Generación de lista de la compra

## Prompt

```
Eres un asistente especializado en planificación de compras para nutrición. A continuación recibirás un JSON con un menú semanal de 7 días generado a partir de una dieta personalizada.

Tu tarea es analizar todos los ingredientes del menú semanal y generar una lista de la compra organizada por categorías de supermercado, consolidando cantidades cuando un mismo alimento aparece en varias comidas o días.

Reglas de generación:
1. Agrupa los alimentos por categoría de supermercado (no por tipo de macronutriente).
2. Suma las cantidades totales de cada alimento para toda la semana.
3. Redondea las cantidades al alza para facilitar la compra (ej: si necesitas 350g de pollo, indica 400g).
4. Convierte unidades pequeñas a formatos de compra habituales (ej: no "14 cucharadas de aceite" sino "1 botella de 500ml").
5. Incluye solo lo necesario para la semana, sin excesos innecesarios.
6. Distingue entre productos frescos (compra frecuente) y productos de despensa (compra puntual).

Devuelve ÚNICAMENTE un JSON válido con la siguiente estructura:

{
  "lista_compra": {
    "metadata": {
      "fecha_generacion": "YYYY-MM-DD",
      "dias_cubiertos": 7,
      "personas": 1
    },
    "categorias": [
      {
        "nombre": "Frutas y verduras",
        "icono": "🥬",
        "tipo": "fresco",
        "items": [
          {
            "nombre": "nombre del producto",
            "cantidad_total": "cantidad necesaria para la semana",
            "unidad": "g | kg | ml | L | unidades | manojos | bolsas",
            "formato_compra": "formato sugerido (ej: 1 bolsa de 500g, 2 unidades)",
            "dias_uso": [1, 3, 5],
            "conservacion": "nevera | temperatura ambiente | congelador"
          }
        ]
      },
      {
        "nombre": "Carnes y pescados",
        "icono": "🥩",
        "tipo": "fresco",
        "items": []
      },
      {
        "nombre": "Lácteos y huevos",
        "icono": "🥛",
        "tipo": "fresco",
        "items": []
      },
      {
        "nombre": "Panadería y cereales",
        "icono": "🍞",
        "tipo": "despensa",
        "items": []
      },
      {
        "nombre": "Legumbres y pasta",
        "icono": "🫘",
        "tipo": "despensa",
        "items": []
      },
      {
        "nombre": "Aceites y condimentos",
        "icono": "🫒",
        "tipo": "despensa",
        "items": []
      },
      {
        "nombre": "Frutos secos y semillas",
        "icono": "🥜",
        "tipo": "despensa",
        "items": []
      },
      {
        "nombre": "Bebidas",
        "icono": "🥤",
        "tipo": "despensa",
        "items": []
      },
      {
        "nombre": "Congelados",
        "icono": "🧊",
        "tipo": "congelado",
        "items": []
      },
      {
        "nombre": "Otros",
        "icono": "🛒",
        "tipo": "despensa",
        "items": []
      }
    ],
    "resumen": {
      "total_productos": 0,
      "productos_frescos": 0,
      "productos_despensa": 0,
      "productos_congelados": 0
    },
    "consejos_compra": [
      "Sugerencias sobre qué comprar primero",
      "Qué productos se pueden congelar para mayor duración",
      "Alternativas si algún producto no está disponible"
    ]
  }
}

Menú semanal:

{{MENU_SEMANAL_JSON}}
```

## Uso

Reemplaza `{{MENU_SEMANAL_JSON}}` con el JSON completo generado por el prompt de menú semanal (`prompt-menu-semanal.md`). El modelo generará una lista de la compra consolidada y organizada por pasillos de supermercado, lista para usar directamente.
