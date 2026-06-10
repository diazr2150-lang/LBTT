# LBTT — Lattice Boltzmann Tensor Train Solver for Photon Transport

Repositorio de notebooks del Trabajo de Fin de Grado:

**"Resolución de la ecuación de Boltzmann para fotones en el rango de energía del radiodiagnóstico mediante un método Lattice Boltzmann en formato tren de tensores"**

*Roberto Díaz Guerra — Grado en Física, Universidad de Cantabria, junio 2026*  
*Director: Enrique Marques*  
*Codirector: Carlos Sainz*

---

## Descripción

Implementación del solver determinista **LBTT** para la Ecuación Lineal de Transporte de Boltzmann (LBTE) de fotones en el rango diagnóstico (1–150 keV). El solver combina el método Lattice Boltzmann con discretización multigrupo (G = 10) y cuadratura S₂₆, y utiliza el formato **Tensor Train (TT-Cross)** para superar la maldición de la dimensionalidad.

El trabajo calcula la fluencia sin colisionar **Ψ^UC** y la primera fuente de dispersión Compton **s^FC** en un fantoma de agua de 30×15×30 cm³ irradiado por una fuente puntual de 100 kVp.

---

## Estructura del repositorio

| Notebook | Contenido |
|---|---|
| `bte_solver_base_S26.ipynb` | Solver LBTT completo con cuadratura S₂₆ |
| `verif_puntual_nist_y_ENDF.ipynb` | Verificación de secciones eficaces puntuales frente a NIST y ENDF/B-VII.1 |
| `verif_multigrupo_todos_los_pesos.ipynb` | Secciones eficaces multigrupo para distintas funciones de peso |
| `iwt1/2/3_sec.ipynb` | Secciones eficaces multigrupo con ponderaciones ITW=1,2,3 |
| `iwt1/2/3_legendre.ipynb` | Momentos de Legendre del kernel Compton para ITW=1,2,3 |
| `TT_UC.ipynb` | Compresión TT-Cross de Ψ^UC en malla gruesa (1 cm) |
| `TT_UC_1mm.ipynb` | Compresión TT-Cross de Ψ^UC en malla fina (1 mm) |
| `TT_FC.ipynb` | Compresión TT-Cross de s^FC en malla gruesa (1 cm) |
| `TT_FC_5mm.ipynb` | Compresión TT-Cross de s^FC en malla intermedia (5 mm) |

---

## Resultados principales

- Secciones eficaces puntuales verificadas frente a NIST con errores **< 0,23 %** (fotoeléctrico) y **< 0,02 %** (Compton)
- Colapso multigrupo verificado frente a NJOY/GAMINR con errores **< 0,2 %** en la sección total
- Compresión TT de Ψ^UC: error de Frobenius **0,0000 %**, factor **16,9×** (1 cm) y **2082,6×** (1 mm)
- Compresión TT de s^FC: factor **182,8×**, error **0,580 %** (1 cm)

---

## Dependencias principales

```python
Python 3.12.7
CuPy 13.6.0 (cuda12x)
NumPy 2.3.4
SpekPy 2.5.3
siddonraytracer (CUDA)
```

---

## Referencia

Memoria completa del TFG disponible en el repositorio de la Universidad de Cantabria.
