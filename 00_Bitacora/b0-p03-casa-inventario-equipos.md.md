# b0-p03 · Casa · Inventario de equipos

- **Alumno:** Lautaro Martin 
- **Bloque:** B0 — Prerrequisitos
- **Fase / ejercicio:** B0.P03 (Fase 0.8)
- **Fecha de inicio:** 26/10/2026
- **Fecha de entrega:** 26/10/2026

---

## 🎯 Qué se pedía

Crear desde cero una bóveda de Obsidian y un repositorio nuevos con un inventario de equipos ficticio. Había que guardarlo en tres versiones con Git y subirlas a GitHub, consultar la primera versión y volver a main. Después había que cerrar la bitácora en un cuarto commit y grabar todo el proceso en vídeo.

## ⌨️ Comandos y pasos importantes

- `git --version` — comprueba que Git está instalado.
- `git config --global user.name` / `user.email` — muestran mi identidad como autor de los commits.
- `ssh -T git@github.com` — comprueba que GitHub me reconoce por SSH.
- `pwd` — muestra la ruta actual, para comprobar que estoy en `01_Proyecto` antes de inicializar.
- `git init` — crea el repositorio (la carpeta `.git`) en `01_Proyecto`.
- `git branch -M main` — fija `main` como nombre de la rama.
- `git remote add origin ...` y `git remote -v` — registran y muestran el remoto de GitHub.
- `git status` — muestra archivos nuevos, modificados y preparados.
- `git add <archivo>` — prepara un archivo concreto para el próximo commit.
- `git diff` — compara el disco con el índice (cambios sin preparar).
- `git diff --cached` (`--stat`) — muestra lo que está preparado para el commit.
- `git commit -m "..."` — guarda una versión local con un mensaje.
- `git push` / `git push -u origin main` — envía los commits a GitHub.
- `git check-ignore -v` — muestra qué regla de `.gitignore` excluye un archivo.
- `git log --oneline` — lista los commits con su código.
- `git switch --detach <código>` — me lleva a un commit antiguo para consultarlo sin cambiar el historial.
- `git switch main` — vuelve a la rama principal.

## 🛠️ Qué he hecho

Primero grabé con OBS y comprobé Git, mi identidad y SSH. Después creé la bóveda `Boveda_Inventario_Casa` fuera de OneDrive y de SOR, con sus carpetas vacías, y creé los archivos iniciales: `.gitignore`, la bitácora, `README.md` y `inventario/equipos.csv`. Comprobé la ruta con `pwd`, hice `git init` en `01_Proyecto`, creé el repositorio vacío `sor-inventario-equipos-casa` en GitHub y añadí `origin` por SSH.

Hice el primer commit con los 4 archivos iniciales y lo subí. En el segundo cambié EQ01 a `Aula-3` y EQ02 a `mantenimiento`, y lo subí también. En el tercero creé la ficha `EQ02.md`, `criterios-estados.md`, una imagen `equipo.png` y la fila EQ03, y actualicé el README. Preparé los archivos uno a uno, revisé el índice con `diff --cached` y comprobé que mis dos clips `.mp4` quedaban ignorados. Hice el commit y lo subí.

Consulté el primer commit (`017df1a`) con `git switch --detach` y vi que EQ01 estaba en Aula-1, EQ02 disponible y EQ03 no existía. Volví a `main` y todo reapareció. Terminé con la comprobación final en GitHub y paré la grabación. Después subí el vídeo, completé esta bitácora y la subí en el cuarto commit.

## 🚩 Qué me ha fallado y cómo lo he resuelto

1. **`.gitignore.txt`:** el editor de texto guardó `.gitignore` como `.gitignore.txt`, así que Git no lo reconocía. Lo renombré desde Git Bash con `mv .gitignore.txt .gitignore` y comprobé con `ls -a`.
2. **Clips `.mp4.mp4`:** los vídeos de prueba se habían guardado como `revision-01.mp4.mp4` y `revision-02.mp4.mp4`. Los renombré con `mv` a `revision-01.mp4` y `revision-02.mp4`, y repetí `git check-ignore -v`.
3. **Enlace roto en el README:** en `git diff` vi que el enlace era `[Inventario](equipos.csv.md)` en vez de `[Inventario](inventario/equipos.csv)` y lo acabe corrigiendo con el comando mv

## 🤔 Respuestas a las preguntas

1. **¿Por qué el repositorio está en `01_Proyecto` y no en la raíz de la bóveda?** Porque la bóveda contiene cosas que no son el producto: la configuración de Obsidian (`.obsidian/`) y las grabaciones de `00_Grabaciones/`. Si hiciera `git init` en la raíz, Git vería todo eso. Con el repositorio solo en `01_Proyecto`, se versiona únicamente el proyecto.

2. **¿Qué dos celdas cambiaste en la segunda versión y cómo se ven en `diff`?** La ubicación de EQ01 (de `Aula-1` a `Aula-3`) y el estado de EQ02 (de `disponible` a `mantenimiento`). En `diff` las líneas antiguas salen con `-` y las nuevas con `+`: `-EQ01,Aula-1,disponible` / `+EQ01,Aula-3,disponible` y lo mismo con EQ02.

3. **¿Qué diferencia hay entre editar una fila y prepararla con `add`?** Editar solo cambia el archivo en el disco. `git add` copia ese cambio al índice, que es la selección de lo que irá en el próximo commit. Hasta que no hay commit, la versión no queda guardada en el historial.

4. **¿Por qué la ficha nueva aparece en `status` y no en el `diff` de `equipos.csv`?** Porque `EQ02.md` es un archivo nuevo sin seguimiento (`??`) y `git diff` solo compara archivos que Git ya conoce. Además, es otro archivo, no forma parte de `equipos.csv`.

5. **¿Qué archivos preparaste individualmente en la ampliación y qué mostró `diff --cached`?** `EQ02.md`, `criterios-estados.md` y `equipo.png` (nuevos, `A`), y `equipos.csv` y `README.md` (modificados, `M`). `diff --cached --stat` mostró exactamente esos 5 archivos (26 inserciones y 2 borrados), la imagen como binario, y ningún `.mp4`.

6. **¿Cómo demostraste que los clips existen y están ignorados sin subirlos?** Con `git status --short --untracked-files=all`, donde no aparecían los `.mp4`, y con `git check-ignore -v`, que mostró la regla `.gitignore:1:*.mp4`. Además los vi en el gestor de archivos, y en GitHub no aparecen.

7. **¿Qué ubicación y estado recuperaste al visitar el primer commit y qué ocurrió con EQ03?** Con `git switch --detach 017df1a`, EQ01 volvió a `Aula-1` y EQ02 a `disponible`. EQ03 no existía, igual que la ficha, los criterios y la imagen. Al volver a `main`, todo reapareció.

8. **¿Por qué este CSV necesita historial y qué limitaciones tiene frente a un inventario multiusuario real?** El historial permite ver qué cambió, cuándo y volver a una versión anterior. Pero un CSV no tiene permisos por usuario, no valida los datos, no permite edición simultánea y Git no garantiza que lo escrito sea verdad. Un inventario real necesita una aplicación o base de datos con esas funciones.

9. **¿Cómo comprobaste la subida de la bitácora y por qué su cierre ocurre después del vídeo?** Lo hice con`git status` y `git log --oneline`, y abre la bitácora en GitHub para ver el contenido y los enlaces.] Se cierra después porque necesita los enlaces reales del vídeo y la playlist, que solo existen cuando el vídeo ya está grabado y subido.

## 🔗 Enlaces

- **Repositorio:**https://github.com/Lauta-Martin-SMR/sor-inventario-equipos-casa
- **Bitácora en GitHub:**https://github.com/Lauta-Martin-SMR/sor-inventario-equipos-casa/tree/main/00_Bitacora
- **Vídeo de esta fase:** https://youtu.be/gPikEMzl9bg
- **Playlist:**https://youtube.com/playlist?list=PLAArGsGkm448&si=_uBo19R_znXsvSGf
## 💭 Dudas / a repasar

ninguna