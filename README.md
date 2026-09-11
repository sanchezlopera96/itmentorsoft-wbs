# Gestor de WBS / EDT — Tutor Inteligente ITM

Aplicación web de una sola página para **visualizar y gestionar** la Estructura de Desglose del Trabajo (WBS / EDT) del proyecto *Tutor Inteligente ITM (ITMentorSoft)*. Permite editar entregables, subentregables y paquetes de trabajo, renumerar los códigos automáticamente (1 → 1.1 → 1.1.1), importar y exportar el Excel, y exportar a PDF.

No requiere servidor ni compilación: es un único `index.html` estático, ideal para **GitHub Pages**.

---

## Publicar en GitHub Pages (opción sin usar la terminal)

1. Entra a <https://github.com> e inicia sesión. Crea un repositorio nuevo con **New → Repository** (por ejemplo `wbs-tutor-itm`). Puede ser público o privado (con privado, Pages requiere plan de pago para verse externamente; para una entrega académica, público suele bastar).
2. En el repositorio vacío, pulsa **Add file → Upload files** y arrastra el contenido de esta carpeta: `index.html`, `.nojekyll` y la carpeta `data/`. Confirma con **Commit changes**.
3. Ve a **Settings → Pages** (menú lateral).
4. En **Build and deployment → Source** elige **Deploy from a branch**. En **Branch** selecciona `main` y la carpeta `/ (root)`. Pulsa **Save**.
5. Espera 1–2 minutos y recarga. GitHub mostrará el enlace público, del tipo:
   `https://TU-USUARIO.github.io/wbs-tutor-itm/`
6. Comparte ese enlace. Cualquiera puede abrir el gestor; los cambios de cada persona se guardan en **su** navegador (ver "Cómo se guardan los datos").

## Publicar con Git (terminal)

```bash
git init
git add .
git commit -m "WBS Tutor Inteligente ITM"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/wbs-tutor-itm.git
git push -u origin main
```

Luego activa Pages como en los pasos 3–5 de arriba.

---

## Uso

- **Tabla (editar):** cambia el nombre de cualquier fila; usa los botones de cada fila para
  `＋` agregar subelemento, `⎘` agregar un elemento hermano debajo, `↑`/`↓` reordenar y `🗑` eliminar.
  Los códigos WBS se recalculan solos.
- **＋ Entregable principal:** agrega una rama nueva de Nivel 1.
- **Diagrama:** vista de árbol con colores por rama.
- **⬆ Importar Excel / ⬇ Exportar Excel / ⬇ CSV:** intercambio de datos con el archivo
  (columnas `Código · Nivel · Entregable/… · Rama`). El Excel es la fuente de datos para respaldar o entregar.
- **🖨 Imprimir / PDF:** imprime el diagrama en A3 horizontal (elige "Guardar como PDF").
- **↺ Restablecer:** vuelve a la versión base incluida.

## Cómo se guardan los datos

Los cambios se guardan en el **almacenamiento local del navegador** (`localStorage`) de quien edita.
Esto significa:

- No se sincronizan automáticamente entre distintas personas ni dispositivos.
- Para compartir un estado concreto, usa **Exportar Excel** y pásalo; la otra persona hace **Importar Excel**.
- Para **edición colaborativa en tiempo real** haría falta un backend (base de datos + API). Mientras
  tanto, el patrón recomendado es mantener el Excel en una unidad compartida (Google Drive / SharePoint)
  como única fuente de verdad, y usar el gestor para editar e importar/exportar.

## Estructura de la carpeta

```
.
├── index.html                     # la aplicación (todo incluido)
├── .nojekyll                      # evita el procesamiento Jekyll de GitHub Pages
├── data/
│   └── WBS_Tutor_Inteligente_ITM.xlsx   # WBS con formato (respaldo de datos)
└── README.md
```

## Notas técnicas

- Librería de Excel: **SheetJS (xlsx)** cargada desde cdnjs (requiere conexión a internet).
- Tipografías: Google Fonts (Sora / Inter); si no hay red, usa las del sistema.
- La rama **4. Pruebas** es la que baja a Nivel 3 en **4.4 Pruebas no funcionales**, agrupando los 14
  requisitos no funcionales por característica de calidad ISO/IEC 25010.
