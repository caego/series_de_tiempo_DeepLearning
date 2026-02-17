# Sesión 5: Estructuras de Redes Profundas para Series de Tiempo Univariadas

## Descripción
Esta sesión explora arquitecturas de redes neuronales profundas especializadas para series temporales univariadas, incluyendo RNN, LSTM y GRU.

## Estructura
- **clases/**: Notebooks con contenido teórico y ejemplos de clase
- **desarrollo/**: Notebooks con ejercicios y proyectos de desarrollo

## Temas
- Redes Neuronales Recurrentes (RNN)
- Long Short-Term Memory (LSTM)
- Gated Recurrent Units (GRU)
- Arquitecturas profundas apiladas
- Manejo de dependencias temporales largas

## Subtemas
5.1. **Análisis de la Serie**
   - Exploración y caracterización de la serie temporal
   - Identificación de patrones de volatilidad
   - Análisis de componentes temporales

5.2. **Ajustar un Modelo LSTM**
   - Construcción de arquitectura LSTM básica
   - Configuración de capas LSTM
   - Entrenamiento del modelo
   - Evaluación de resultados iniciales

5.3. **Ajustar un LSTM con Early Stopping**
   - Implementación de Early Stopping
   - Monitoreo de métricas de validación
   - Prevención de overfitting
   - Guardado del mejor modelo

5.4. **Comparar con un Modelo Clásico GARCH**
   - Introducción al modelo GARCH
   - Ajuste del modelo GARCH
   - Comparación de predicciones
   - Análisis de ventajas y desventajas

5.5. **Resultados Comparativos en el Conjunto de Test**
   - Evaluación en datos de prueba
   - Métricas de comparación (RMSE, MAE, etc.)
   - Análisis de errores
   - Conclusiones finales
