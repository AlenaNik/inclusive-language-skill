# Inclusive Language — Skill para Claude

Plugin de Claude que añade la skill **`inclusive-language`**: ayuda a escribir y revisar textos de un proyecto (textos de interfaz, documentación, READMEs, mensajes de error, marketing, comentarios de código) con un lenguaje inclusivo y accesible, y propone alternativas respetuosas.

Está basada en la [guía de lenguaje inclusivo de Reedsy](https://reedsy.com/blog/inclusive-language/), adaptada a la escritura de producto y de proyectos.

## Qué hace

- **Al escribir texto nuevo**: textos de interfaz, onboarding, emails, artículos de ayuda, notas de versión, páginas de marketing, texto alternativo y comentarios de código.
- **Al revisar** un diff, un documento o un conjunto de textos: señala cada problema con la frase exacta, su categoría, por qué puede excluir o hacer daño, y una o dos alternativas concretas.
- **Responde a preguntas** como "¿está bien esta frase?" o "hazlo más inclusivo".

### Áreas que cubre

| Área | Ejemplos |
|---|---|
| Raza, etnia y nacionalidad | *Oriental* → *Asian* o la nacionalidad concreta; *mixed race* → *multiracial* |
| Género, sexo y sexualidad | *chairman* → *chair*; *guys* → *everyone*, *team*; uso de *they* en singular |
| Discapacidad y neurodiversidad | *wheelchair-bound* → *wheelchair user*; *crippling the build* → *blocking the build*; *sanity check* → *quick check* |
| Exclusión implícita | Frases con "nosotros" o "todo el mundo" que dan por hecho una sola experiencia |

### Principios

1. Mirar más allá de lo evidente.
2. Mencionar la identidad solo cuando sea relevante.
3. Priorizar la precisión y la neutralidad.
4. Preguntar en lugar de suponer.
5. Pedir una segunda revisión en contenido sensible.

### Formato de revisión

```
- "<frase>" (archivo:línea o ubicación)
  Category: <categoría>
  Why: <una frase>
  Suggest: "<alternativa>"
```

Al final da un resumen con el número de problemas por categoría y los puntos que necesitan una decisión humana. En el código, avisa del impacto de compatibilidad (alias, deprecación) antes de proponer renombrar identificadores o APIs públicas.

## Estructura

```
.
├── .claude-plugin/
│   └── plugin.json              # Metadatos del plugin
└── skills/
    └── inclusive-language/
        └── SKILL.md             # Instrucciones de la skill
```

## Instalación

### Claude Code (como plugin)

Clona el repositorio y añádelo como plugin local:

```bash
git clone https://github.com/AlenaNik/inclusive-language-skill.git
```

```bash
claude --plugin-dir ./inclusive-language-skill
```

### Claude Code (solo la skill)

Copia la carpeta de la skill en tus skills personales o en las del proyecto:

```bash
cp -r skills/inclusive-language ~/.claude/skills/
```

### Claude.ai

Comprime la carpeta `skills/inclusive-language` en un `.zip` y súbela en **Settings → Capabilities → Skills**.

## Uso

Claude activa la skill automáticamente cuando escribes o revisas texto. También puedes pedirlo de forma directa:

- "Revisa el README con la skill de lenguaje inclusivo."
- "¿Es inclusivo este mensaje de error?"
- "Reescribe este texto de onboarding para que sea más inclusivo."

## Recursos

- [Conscious Style Guide](https://consciousstyleguide.com/)
- [Diversity Style Guide](https://www.diversitystyleguide.com/)
- [18F Content Guide: Inclusive language](https://content-guide.18f.gov/our-style/inclusive-language/)
- [NLGJA Stylebook](https://www.nlgja.org/stylebook/)
- [GLAAD Media Reference Guide](https://glaad.org/reference/)
