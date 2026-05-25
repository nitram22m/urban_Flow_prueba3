
## Conclusión - Sprint 2

### Relación entre imágenes y datos tabulares

El cruce entre las imágenes de los radares y el dataset
del Sprint 1 permite validar qué multas cuentan con
evidencia visual. El resultado depende directamente de la
calidad del OCR aplicado a cada imagen.

### Pipeline de procesamiento

El pipeline implementado (grises, blur, cierre morfológico
rectangular, umbralización OTSU y recorte por contornos)
mejora significativamente la legibilidad del texto respecto
a trabajar sobre las imágenes originales. El filtrado
geométrico por área y relación de aspecto (2.0 a 6.5)
permite aislar regiones de patente con precisión razonable.

### Impacto de los datos inválidos (00:00 y 1932-01-01)

Las filas con hora 00:00 y fecha 1932-01-01 provienen del
proceso de normalización del Sprint 1. Representan datos
cuyo valor temporal original no pudo parsearse. Estas filas
participan del cruce con imágenes y pueden tener imagen
asociada, pero sus metadatos de hora y fecha no son
confiables para análisis cronológico. Son un porcentaje
relevante del dataset y sesgan cualquier métrica por
franja horaria o período mensual.

### Multas sin evidencia visual

Una fracción del dataset no pudo asociarse a ninguna imagen.
Esto puede deberse a: falta de imagen para esa infracción,
fallo de OCR que produce texto vacío o sin coincidencia, o
variaciones de formato entre la patente del dataset y la
detectada visualmente. Para mejorar el porcentaje de
matches se recomienda explorar umbrales de ratio más
flexibles o técnicas OCR especializadas en patentes.

### Conclusión general

El sistema del Sprint 2 establece un puente entre la
evidencia fotográfica y los registros administrativos.
La integración de ambas fuentes (tabular + visual) sienta
las bases para un sistema de multas más robusto, donde
cada infracción pueda ser validada y auditada visualmente.
