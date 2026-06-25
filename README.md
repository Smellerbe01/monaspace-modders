# Monaspace Remix: NeiberFonts 🚀

[![GitHub license](https://img.shields.io/github/license/github-user/repo-name)](LICENSE)
[![FontForge](https://img.shields.io/badge/Made%20with-FontForge-blue.svg)](https://fontforge.org/)

**Monaspace Remix (NeiberFonts)** es una familia de fuentes tipográficas híbrida diseñada para maximizar la legibilidad y la estética en entornos de desarrollo. A diferencia de las familias tradicionales donde los estilos (*Italic*, *Bold*) son solo variaciones de peso de la misma tipografía, este proyecto utiliza una **fusión por metadatos** realizada en **FontForge** para enlazar 4 fuentes completamente distintas y diferenciables bajo un mismo nombre.

La magia de **NeiberFonts** se activa mediante la configuración del archivo de preferencias (como el `.json` de tu editor de código). Al asignar estilos específicos a diferentes elementos sintácticos (como comentarios o palabras clave), el editor no solo cambia el peso del texto, sino que intercambia la fuente por una familia visualmente diferente en tiempo real.

---

## 🛠️ Arquitectura de la Familia Tipográfica

El proyecto consta de **4 archivos de fuentes** enlazados internamente mediante metadatos para funcionar en perfecta sincronía dentro de tu editor:

| Estilo del Sistema | Fuente Real Asignada | Propósito Sugerido en el Editor |
| :--- | :--- | :--- |
| **Normal (Regular)** | **Argon** | Fuente base por defecto para el cuerpo general del código. |
| **Italic** | **Xenon** | Aplicado a **comentarios**. Cambia a una fuente completamente diferente y muy diferenciable del resto. |
| **Bold** | **Radon** | Aplicado a **palabras clave o funciones**, otorgando un resalte estructural único. |
| **Bold Italic** | **Krypton** | Variante híbrida para casos especiales de sintaxis avanzada o variables clave. |

---
![Vista previa ](monaspace-modders/code.png)

## 🚀 Instalación y Configuración

### 1. Instalación de las Fuentes

Para disfrutar de la experiencia híbrida, debes instalar los 4 archivos en tu sistema para que actúen como una sola familia:

1. Descarga los 4 archivos de fuente desde la carpeta `fonts/` de este repositorio.
2. Instálalos en tu sistema operativo (en Windows: clic derecho e "Instalar para todos los usuarios"; en macOS: añadir al Catálogo Tipográfico).

### 2. Configuración en el Editor (Ejemplo para VS Code)

Una vez instaladas, la segmentación visual se logra editando el archivo de configuración `settings.json`.

Por ejemplo, para activar **Argon** por defecto y hacer que los comentarios adopten la fuente **Xenon** automáticamente mediante el estilo *Italic*, añade lo siguiente a tu `.json`:

Puedes usar este archivo como referencia, no olvides cambiar la linea del tema que esta utilizando, en mi caso es el Aura Soft Dark:

los tokens se pueden obtener inspeccionando el editor mediante las opciones de desarrollador: inspeccionar los tokens y ámbitos del editor. Lo encuentras usando ctrl + shift + p, luego buscas "inspect"

```json
// --- 🖋️ CONFIGURACIÓN DE FUENTES MONASPACE MIX ---

    "editor.fontFamily": "'NeiberFonts', 'Consolas', 'Courier New', monospace",
    "editor.fontSize": 13.3,
    "editor.fontLigatures": true,
    "editor.fontWeight": "400",

// --- 🎨 PERSONALIZACIÓN TIPOGRÁFICA Y DE SINTAXIS (SQL, PYTHON, HTML, CSS, JS) ---
"editor.tokenColorCustomizations": {
    "[Aura Soft Dark]": { //modificalo según tu tema de vscode
        "textMateRules": [

            // ==========================================
            // 1. ELEMENTOS COMUNES Y COMENTARIOS
            // ==========================================

            // 🟢 XENON (Italic) - Comentarios generales y de bases de datos
            {
                "scope": [
                    "comment",
                    "punctuation.definition.comment",
                    "source.sql comment",
                    "source.pgsql comment",
                    "comment.line.number-sign.python"
                ],
                "settings": {
                    "foreground": "#00ff80",
                    "fontStyle": "italic" 
                }
            },

            // 🔢 XENON (Italic) - Constantes numéricas
            {
                "scope": [
                    "constant.numeric",
                    "constant.numeric.sql"
                ],
                "settings": {
                    "foreground": "#00FFBC",
                    "fontStyle": "italic"
                }
            },

            // 🔗 RADON (Bold) - Operadores lógicos y matemáticos
            {
                "scope": [
                    "keyword.operator"
                ],
                "settings": {
                    "foreground": "#ffffff",
                    "fontStyle": "bold"
                }
            },


            // ==========================================
            // 2. PALABRAS CLAVE Y STRUCTS (KEYWORDS CENTRALES)
            // ==========================================

            // ⚡ KRYPTON (Bold Italic) / RADON (Bold) - Estructuras de control, DDL y DML (SQL & Python)
            // Nota: Al heredar "bold" se mapea a Radon, pero las estructuras principales toman fuerza aquí.
            {
                "scope": [
                    "keyword.control",
                    "keyword.other.sql",
                    "source.sql keyword",
                    "source.pgsql keyword",
                    "keyword.other.DML.sql",
                    "keyword.other.DDL.sql",
                    "keyword.other.create.sql",
                    "keyword.other.DDL.create.sql",
                    "keyword.control.sql",
                    "keyword.control.conditional.sql",
                    "keyword.other.alias.sql",
                    "keyword.other.DDL.create.II.sql",
                    "keyword.control.flow.python",
                    "storage.type",
                    "storage.modifier"
                ],
                "settings": {
                    "foreground": "#00FFBC",
                    "fontStyle": "bold" 
                }
            },


            // ==========================================
            // 3. CORE PYTHON (LÓGICA, DOCSTRINGS Y REGEX)
            // ==========================================

            // 💎 KRYPTON (Bold Italic) - Docstrings de Python (Comentarios de documentación fucsia)
            {
                "scope": [
                    "string.quoted.docstring.multi.python"
                ],
                "settings": {
                    "foreground": "#ff0fcb",
                    "fontStyle": "bold italic"
                }
            },

            // 📦 ARGON (Regular) - Palabras clave del ecosistema Python (Imports, constantes y parámetros)
            {
                "scope": [
                    "keyword.control.import.python",
                    "constant.language.python",
                    "variable.parameter.function.language.python",
                    "variable.parameter.function-call.python"
                ],
                "settings": {
                    "foreground": "#ce95fe"
                }
            },

            // 🔗 XENON (Italic) - Expresiones regulares (Regex) y enlaces internos en Python
            {
                "scope": [
                    "string.regexp.quoted.single.python"
                ],
                "settings": {
                    "foreground": "#e1ff01",
                    "fontStyle": "italic"
                }
            },

            // 📄 ARGON (Regular) - Strings específicos de Python (comillas simples)
            {
                "scope": [
                    "string.quoted.single.python"
                ],
                "settings": {
                    "foreground": "#01e6ff"
                }
            },


            // ==========================================
            // 4. FUNCIONES, MÉTODOS Y TEXTOS (STRINGS)
            // ==========================================

            // 📄 ARGON (Regular) - Cadenas de texto (Strings generales SQL y comillas dobles en Python)
            {
                "scope": [
                    "string.quoted.single.sql",
                    "string.quoted.double.sql",
                    "string.quoted.double.python",
                    "meta.function-call.arguments.python",
                    "constant.other.table-name.sql",
                    "constant.other.database-name.sql"
                ],
                "settings": {
                    "foreground": "#ffffff"
                }
            },

            // 🛠️ ARGON (Regular) - Definición y llamadas de funciones o métodos
            {
                "scope": [
                    "entity.name.function",
                    "entity.name.function.sql",
                    "entity.name.function.python",
                    "meta.function-call.generic.python",
                    "meta.function-call.python"
                ],
                "settings": {
                    "foreground": "#ffffff"
                }
            },


            // ==========================================
            // 5. DESARROLLO WEB (HTML, CSS y JAVASCRIPT)
            // ==========================================

            // ⚡ RADON (Bold) - Etiquetas principales y selectores clave (HTML, CSS, JS, y constantes de Python)
            {
                "scope": [
                    "entity.name.tag.html",
                    "entity.name.tag.css",
                    "entity.name.tag.js",
                    "constant.other.caps.python"
                ],
                "settings": {
                    "foreground": "#00FFBC",
                    "fontStyle": "bold"
                }
            },

            // 🔗 XENON (Italic) - Puntuación de etiquetas HTML y selectores estructurales de CSS
            {
                "scope": [
                    "punctuation.definition.tag.end.html",
                    "punctuation.definition.tag.begin.html",
                    "meta.tag.structure.section.end.html",
                    "entity.name.tag.css",
                    "meta.selector.css"
                ],
                "settings": {
                    "foreground": "#ffffff",
                    "fontStyle": "italic"
                }
            },

            // 🔗 XENON (Italic) - Atributos, enlaces y textos en comillas dobles (HTML y JavaScript)
            {
                "scope": [
                    "string.quoted.double.html",
                    "string.quoted.double.js"
                ],
                "settings": {
                    "foreground": "#6ede83",
                    "fontStyle": "italic"
                }
            },

            // 📄 ARGON (Regular) - Propiedades y objetos de JavaScript
            {
                "scope": [
                    "variable.other.property.js"
                ],
                "settings": {
                    "foreground": "#01e6ff"
                }
            }

        ]
    }
},
