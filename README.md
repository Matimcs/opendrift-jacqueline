# Modelo de Dispersión OpenDrift — Centro Jacqueline, Canal Costa

**Curso:** Transporte en Sistemas Acuáticos · FCFM Universidad de Chile  
**Proyecto:** Centro de Engorda Jacqueline · Pert 201111284 · Pacific Seafoods S.A.  

---

## ▶ Abrir en Google Colab

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://githubtocolab.com/Matimcs/opendrift-jacqueline/blob/main/OpenDrift_final.ipynb)

---

## Descripción

Notebook de Python para simular la dispersión y deposición de material particulado (pellets de alimento no consumido y fecas) en el lecho marino del Canal Costa, usando el modelo lagrangiano **OpenDrift**.

### Qué hace el notebook

| Sección | Contenido |
|---------|-----------|
| Calibración | Compara corrientes CMEMS vs ADCP (RMSE, Bias, Willmott d) |
| Validación DGA | Caudal Río Aysén estación 11342001-4 · Riₑ ≈ 3 (estratificación moderada) |
| Simulación CMEMS | Ciclo 1 + 2 con forzante de reanálisis global |
| **Simulación ADCP** | **Ciclo 1 + 2 con forzante de correntometría in-situ** |
| Mapas de calor | Deposición acumulada kg/m² sobre batimetría real |

### Resultados principales

- **Ciclo 1 ADCP (14 meses):** deposición máxima 0,031 kg/m² · 100% partículas depositadas  
- **Ciclo 2 ADCP (28 meses acumulados):** deposición máxima 0,062 kg/m²  
- Circulación estuarina bicapa: superficie → ENE (70°) · fondo → SSW (220°)

---

## Archivos del repositorio

```
OpenDrift_final.ipynb   ← notebook principal (49 celdas)
batimetria.csv          ← 103 puntos de ecosonda (EIA, Aquatecma 2008)
README.md
```

---

## Instrucciones de ejecución

### Google Colab (recomendado — sin instalación)

1. Hacer clic en el botón **"Abrir en Colab"** arriba  
2. Ejecutar la **Celda 2** (instalación de dependencias, ~5 min)  
3. Ir a **Entorno de ejecución → Reiniciar sesión**  
4. Ejecutar todo: **Entorno de ejecución → Ejecutar todo**  
5. Ingresar credenciales **Copernicus Marine** cuando se soliciten

> El notebook detecta automáticamente que está en Colab y descarga `batimetria.csv` desde este repositorio. No hay que subir nada a mano.

### VS Code / local (Windows)

1. Crear la carpeta `C:\OPENDRIFT\`  
2. Copiar `batimetria.csv` a `C:\OPENDRIFT\batimetria.csv`  
3. Abrir `OpenDrift_final.ipynb` en VS Code  
4. Ejecutar **Celda 2** → reiniciar kernel → **Run All**

---

## Requisitos

- **Cuenta Copernicus Marine** (gratuita): [marine.copernicus.eu](https://marine.copernicus.eu)  
  Se usa para descargar datos de corrientes CMEMS (~70 MB, solo la primera vez)
- Python ≥ 3.10 (instalado automáticamente en Colab)

### Dependencias (instaladas por Celda 2)

```
opendrift · copernicusmarine · scipy · pyproj · xarray · netCDF4 · matplotlib · numpy · pandas
```

---

## Datos utilizados

| Dato | Fuente | Uso |
|------|--------|-----|
| ADCP Sontek ADP 500 kHz | EIA Aquatecma 2008 (Anexo B) | Calibración / forzante simulación |
| Corrientes CMEMS | Copernicus Marine (GLORYS12) | Forzante reanálisis global |
| Batimetría 103 pts | CPS / Subpesca | Detección de fondo marino |
| Caudal Río Aysén | DGA, estación 11342001-4 | Escala estacional del forzante ADCP |
| Balance de masas | Adenda N°1 EIA | Conversión partículas → kg/m² |

---

## Referencia rápida de figuras generadas

| Figura | Descripción |
|--------|-------------|
| `fig_calibracion.png` | Perfil vertical CMEMS vs ADCP + scatter 1:1 |
| `fig_histograma_validacion.png` | Distribución de velocidades por capa |
| `fig_dga_caudal.png` | Variación estacional Río Aysén (DGA) |
| `fig_rosa_corrientes.png` | Rosa de corrientes observadas |
| `fig_deposicion_kg_m2.png` | Mapa deposición cuadratura (24h) |
| `fig_heatmap_adcp_acumulacion.png` | **Mapa de calor Ciclo 1 vs Ciclo 2 (ADCP)** |
| `fig_heatmap_adcp_evolucion.png` | **Evolución temporal deposición máxima** |
| `fig_comparacion_EIA.png` | OpenDrift vs DEPOMOD (EIA) |
| `fig_escenarios_acumulacion.png` | Escenarios acumulación CMEMS |
