# wellcore-exercise-gifs-v2

Catálogo oficial **v2** de GIFs de ejercicios de WellCore Fitness — usado por el motor v2 de generación de planes.

## Características

- **220 GIFs curados** con nombres consistentes (lowercase, separados por guiones, sin espacios).
- Reemplaza al repo anterior `wellcore-exercise-gifs` (que tenía 265 entries con nombres inconsistentes y archivos extras no validados).
- Tamaño total: ~137 MB.

## URL canónica

```
https://raw.githubusercontent.com/analyticfitness-design/wellcore-exercise-gifs-v2/main/{filename}.gif
```

Ejemplo:

```
https://raw.githubusercontent.com/analyticfitness-design/wellcore-exercise-gifs-v2/main/press-banca-barra.gif
```

## Uso en el motor v2

El motor v2 (`wellcore-laravel`) lo consume vía `app/Models/Kb/ExerciseMetadata::gifUrl()`. La URL base está hardcodeada — **no aceptamos URLs de otros repos** para garantizar consistencia.

Si querés agregar un GIF nuevo:
1. Cargá el archivo en la raíz de este repo (lowercase + guiones, sin espacios).
2. Corré `kb:verify-gifs --force` en el motor v2 para que reconozca el nuevo status.
3. Agregá un row en `wellcore_kb.exercise_metadata` con `alias` = nombre del archivo sin `.gif`.

## Política de cambios

- Los archivos en este repo son **inmutables** una vez subidos. Para reemplazar un GIF, crear un alias nuevo (no sobrescribir el archivo viejo) → los planes históricos de clientes siguen rindiendo igual.
- Los nombres NUNCA llevan mayúsculas, espacios ni caracteres especiales. Solo `a-z`, `0-9`, y `-`.
