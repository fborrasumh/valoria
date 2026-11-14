# ValorIA

Del diagnóstico facial por tercios y por capas a un plan por fases. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/valoria/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24214890.svg)](https://doi.org/10.5281/zenodo.24214890)

**Idiomas:** español (por defecto), inglés y portugués. Se cambian con el selector de la barra superior o con `?lang=en` / `?lang=pt` en la URL.

## Qué hace

Es la segunda app del [Kit EstéticIA](https://fborrasumh.github.io/kitesteticia/). Va después de AnamnesIA y antes de ConsentIA y PautIA.

1. **Paciente y piel.** Recoge lo que preocupa a la paciente, el fototipo de Fitzpatrick, el grado de Glogau, la laxitud y la calidad de la piel. Puede cargar la ficha de AnamnesIA (`kitesteticia-paciente/1`), de la que toma:
   - el identificador y el fototipo;
   - las técnicas desaconsejadas o en precaución;
   - el cribado de trastorno dismórfico.
2. **Exploración.** Recorre 15 zonas en cuatro bloques (tercio superior, medio e inferior, y cuello y submentón). Cada zona se puntúa de 0 a 4 en reposo y con el gesto, y se marca la capa que lo causa: piel, grasa, músculo o hueso y soporte. El esquema facial se colorea por gravedad.
3. **Plan por fases.** Las zonas puntuadas con 2 o más que tienen una capa marcada pasan al plan, en tres fases:
   - Fase 1, soporte: sienes, pómulos, mentón y mandíbula.
   - Fase 2, gesto y contorno.
   - Fase 3, piel.

   El plan avisa en estos casos:
   - Trata el soporte antes que el surco: cuando el surco nasogeniano, la ojera o las líneas de marioneta dependen del pómulo o de la mandíbula, propone reevaluar el surco a las 4 semanas.
   - Fototipo IV a VI con láser o peeling.
   - Laxitud importante, con el límite que tienen los tratamientos médicos.
   - Lo que desaconseja AnamnesIA.

   Cada propuesta muestra su zona de riesgo: las arterias y estructuras que hay que respetar. Lleva también un presupuesto con tus precios.
4. **Documentos en Word.**
   - El plan para la paciente, en su idioma y en lenguaje llano, sin la jerga de los riesgos.
   - El informe de valoración para la historia clínica, con las zonas de riesgo y las referencias.

No usa IA y no hace ninguna llamada de red. Las propuestas salen de reglas escritas: la indicación y el plan definitivo son del médico.

## Referencias

- Fitzpatrick (1988), Glogau (1996) y Flynn et al. (2012, escalas Merz).
- Rohrich y Pessa (2007), sobre los compartimentos grasos.
- Mendelson y Wong (2012), sobre el esqueleto facial.
- Scheuer et al. (2017), sobre las zonas de riesgo.
- de Maio (2021), MD Codes.

## Límites

Es una herramienta de apoyo para médicos con formación en medicina estética. No sustituye el juicio clínico, las fichas técnicas ni la formación práctica en anatomía.

## Pruebas

- `node tests/test_nucleo.js` comprueba:
  - el soporte antes que el surco;
  - el umbral de gravedad, las alternativas y la exclusión;
  - la fusión de capas con la misma técnica;
  - la piel, el fototipo y la laxitud;
  - la lectura de la ficha de AnamnesIA, el presupuesto y los documentos;
  - los tres idiomas.
- `python3 tests/smoke.py` hace el recorrido completo:
  - la ficha de AnamnesIA y el mapa interactivo;
  - el plan editable y el presupuesto;
  - los dos documentos en Word y la persistencia;
  - los tres idiomas, la accesibilidad WCAG 2.2 AA, la política de seguridad (CSP) y el móvil.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y Elena Caride Miana (Dra. Caride Medicina Estética & Antiaging).

Segunda app del Kit EstéticIA, diseñado para el alumnado del Máster de Formación Permanente en Medicina Estética Integral y Antienvejecimiento (UMH).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · Elena Caride Miana [0000-0002-7620-4857](https://orcid.org/0000-0002-7620-4857)

## Cómo citar

Borrás Rocher, F. y Caride Miana, E. (2026). *ValorIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.24214890](https://doi.org/10.5281/zenodo.24214890)

## Licencia

MIT. Véase [LICENSE](LICENSE).
