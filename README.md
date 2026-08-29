# Simulador de Gestión de Procesos y Memoria (TPI-SO)

![Python Version](https://img.shields.io/badge/python-3.10%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)

Simulador interactivo de administración de CPU y memoria para Sistemas Operativos. El sistema implementa el algoritmo de planificación **SRTF** (*Shortest Remaining Time First*) y la política de asignación de memoria **Best-Fit** (*Mejor Ajuste*) sobre esquemas de particiones fijas.

---

## 📌 Características Principales

* ⏱️ **Algoritmo de Planificación SRTF (Apropiativo)**: Interrupción de procesos en ejecución si ingresa un proceso listo con menor tiempo restante de CPU.
* 🧠 **Gestión de Memoria Best-Fit**: Asignación óptima de particiones fijas calculando fragmentación interna.
* 📊 **Grado de Multiprogramación Regulado**: Límite de hasta 5 procesos concurrentes simultáneos en memoria (con soporte para estado *Listo y Suspendido*).
* 📁 **Carga Dinámica por CSV**: Importación de lotes de procesos mediante selector gráfico de archivos (`Tkinter`).
* 🎨 **Interfaz de Consola Enriquecida**: Renderizado en tiempo real con tablas dinámicas a color mediante la biblioteca `rich`.
* 📈 **Estadísticas Finales**: Cálculo automático del tiempo de retorno promedio, tiempo de espera promedio y rendimiento del sistema.

---

## 📐 Esquema de Memoria

La memoria principal está configurada de forma estática con un tamaño total y particiones predefinidas:

| Partición | Dir. Inicio | Tamaño (K) | Estado / Uso Inicial |
| :---: | :---: | :---: | :--- |
| **0 (SO)** | `0` | 100K | Reservado para el Sistema Operativo |
| **1** | `100` | 250K | Disponible para procesos |
| **2** | `350` | 150K | Disponible para procesos |
| **3** | `500` | 50K | Disponible para procesos |

---

## 📁 Estructura del Proyecto

```text
.
├── consola.py           # Funciones de lectura/parsing de CSV e impresión en consola
├── memoria.py           # Definición de particiones fijas y validación de tamaño
├── planificador.py      # Implementación del algoritmo Best-Fit y ordenamiento SRTF
├── procesos.py         # Clase Proceso y gestión de sus estados y tiempos
├── rich_simulador.py    # Interfaz gráfica de consola (UI) y bucle principal de simulación
└── data/                # Archivos CSV de prueba (lotes de procesos)
    ├── Lote1.csv
    ├── Lote2.csv
    ├── Lote3.csv
    ├── Procesos.csv
    └── Procesos_SRTF.csv
```

---

## 🚀 Requisitos e Instalación

### Requisitos Previos
* Python **3.10** o superior.
* `tkinter` (usualmente incluido en las instalaciones estándar de Python).

### Instalación de Dependencias

Clona el repositorio e instala la biblioteca `rich`:

```bash
git clone https://github.com/LucaV10/TPI-SO.git
cd TPI-SO
pip install rich
```

---

## 🖥️ Uso del Simulador

Para ejecutar la simulación en modo interactivo:

```bash
python rich_simulador.py
```

1. Se abrirá automáticamente una ventana de diálogo para seleccionar el archivo `.csv` con la lista de procesos (puedes utilizar cualquier archivo de la carpeta `data/`).
2. Presiona `[Enter]` en la terminal para avanzar la simulación paso a paso (UT por UT).
3. Al finalizar, la consola mostrará la tabla de tiempos y el resumen de estadísticas de rendimiento.

---

## 📄 Formato del Archivo CSV de Procesos

Los archivos `.csv` deben contener los siguientes encabezados:

```csv
proceso_id,t_arribo al sistema,memoria_K,tiempo_irrupcion
P1,0,120,6
P2,1,40,3
P3,2,200,8
```

---

## 📜 Licencia

Proyecto desarrollado para la asignatura **Sistemas Operativos** (UTN). Libre para fines educativos.
