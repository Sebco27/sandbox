# Script de Evaluación de Algoritmos

Script automatizado en Bash para evaluar algoritmos implementados por estudiantes en respuesta de los ejercicios planteados en cada laboratorio. Realiza compilación, ejecución y comparación de resultados contra salidas esperadas de manera automatizada.

## Estructura de Directorios Requerida

```
└── Lab[número_lab]/
    ├── testLab.sh                 # Script principal
    ├── Files/                     # Entregables de estudiantes
    │   ├── estudiante1.zip        # Archivos comprimidos con código
    │   ├── estudiante2.zip
    │   └── ...
    ├── Inputs/                    # Casos de prueba de entrada
    │   └── L[número_ejercicio]/   # Organizados por ejercicio
    │       ├── test1.txt
    │       ├── test2.txt
    │       └── ...
    ├── Expecteds/                 # Resultados esperados
    │   └── L[número_ejercicio]/   # Misma estructura que Inputs
    │       ├── test1.txt
    │       └── ...
    └── Outputs/                   # Generados automáticamente
        └── [estudiante]/
            └── L[número_ejercicio]/
                ├── test1.txt
                └── ...
```

## Uso

### Preparación previa:
1. Colocar archivos ZIP de estudiantes en `Files/`
2. Preparar casos de prueba en `Inputs/`
3. Preparar resultados esperados en `Expecteds/`

> [!NOTE]
> Los archivos ZIP deben contener el código fuente y un Makefile y deben seguir el formato de nombre `[Apellido1][Apellido2][Nombre].zip`.

### Ejecución:
```bash
chmod +x testLab.sh
./testLab.sh
```

## Requisitos del Sistema

- **Sistema Operativo**:
  - Linux
  - MacOS puede fallar por el uso de `timeout`
- **Dependencias**:
  - `bash` (shell)
  - `unzip` (descompresión)
  - `make` (compilación)
  - `timeout` (gestión de tiempos)
  - `diff` (comparación de archivos)

## Funcionalidades

### Proceso Automatizado
1. **Descompresión** de archivos ZIP de estudiantes
2. **Compilación** automática de archivos `.cpp`
3. **Ejecución** de binarios con casos de prueba
4. **Comparación** con resultados esperados
5. **Generación** de reportes detallados

### Métricas Recopiladas
- Resultados de pruebas (éxito/fallo)
- Tiempos de ejecución
- Conteos de buenas/malas/totales
- Detección de timeouts

## Estructura de Reportes

Cada estudiante genera un archivo `.txt` con:
```
[Nombre] [Apellido] [SegundoApellido]
Resultados de pruebas:
[ejercicio]:
[caso_prueba]: [resultado]
[tiempo_ejecución]
...
----------
Buenas: [cantidad]
Malas: [cantidad]
Total: [cantidad]
----------
```

## Output Generado

- **`Outputs/`**: Contiene las salidas generadas por cada estudiante
- **`Files/[estudiante]/[estudiante].txt`**: Reporte individual detallado
- **Directorios descomprimidos**: En `Files/` con el nombre del estudiante

---

*Este script está diseñado para entornos educativos de evaluación automatizada de algoritmos.*
