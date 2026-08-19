# Simulador HPLC Didàctic Avançat

Aquest projecte és un simulador educatiu de Cromatografia Líquida d'Alta Resolució (HPLC) desenvolupat en JavaScript pur (Vanilla JS), HTML i estilitzat amb Tailwind CSS. Està dissenyat com una eina didàctica per a estudiants de cicles formatius com el de "Laboratori d'Anàlisi i de Control de Qualitat", permetent explorar conceptes clau de la cromatografia de manera interactiva i visual.

El simulador es presenta en un únic fitxer `cromatografia4.html` per a la seva fàcil distribució i ús sense necessitat d'un servidor web.

## Característiques Principals

El simulador permet a l'usuari ajustar una àmplia gamma de paràmetres cromatogràfics i observar-ne l'efecte en temps real sobre el cromatograma resultant.

### 1. Paràmetres del Mètode

- **Fase Mòbil:**
  - **Mode Isocràtic:** Composició constant de la fase mòbil.
  - **Mode de Gradient:** Programació d'un gradient lineal, definint el percentatge inicial i final de dissolvent orgànic (%B) i el temps del gradient.
  - **pH de la Fase Mòbil:** Ajust del pH del tampó aquós, crucial per a la separació de compostos ionitzables.
- **Bomba i Forn:**
  - **Flux:** Control del cabal de la fase mòbil (mL/min).
  - **Temperatura:** Ajust de la temperatura de la columna, que afecta la viscositat i la retenció.

### 2. Maquinari Virtual

- **Tipus de Columna:** Permet seleccionar diferents fases estacionàries (C18, C8, Fenil), cadascuna amb la seva pròpia eficiència i selectivitat.
- **Longitud de Columna:** Diferents longituds de columna (50, 100, 150, 250 mm) que afecten la resolució, el temps d'anàlisi i la contrapressió.

### 3. Mostres i Anàlits

- **Selecció de Mostres:** Inclou diverses mescles predefinides amb compostos d'interès real:
  - Aditius Alimentaris
  - Fàrmacs Analgèsics
  - Vitamines Hidrosolubles
- **Compostos Ionitzables:** Algunes mostres contenen compostos amb pKa definit, la retenció dels quals és altament dependent del pH.

### 4. Anàlisi de Dades Avançat

- **Cromatograma Interactiu:** Visualització del cromatograma en format SVG, amb actualització en temps real durant la simulació.
- **Taula de Resultats:** Integració automàtica dels pics, mostrant:
  - Temps de Retenció ($t_R$)
  - Amplada de Pic
  - Factor de Capacitat ($k'$)
  - **Resolució ($R_s$)** entre pics adjacents, destacant la resolució crítica.
- **Monitor de Pressió:** El sistema calcula i mostra la contrapressió en temps real, generant un error de "SOBREPRESSIÓ" si se supera el límit de 400 bar.

### 5. Mòduls Addicionals

- **Corba de Calibració:**
  - Permet realitzar injeccions d'un estàndard a diferents concentracions.
  - Genera automàticament una corba de calibració (Alçada de pic vs. Concentració).
  - Calcula i mostra l'equació de la recta de regressió i el coeficient de determinació ($R^2$).
- **Test de Robustesa:**
  - Executa una anàlisi automàtica per avaluar la robustesa del mètode.
  - Simula petites variacions ($\pm \Delta$) en paràmetres clau (flux, pH, %B, temperatura).
  - Presenta un informe que quantifica la desviació percentual en el temps de retenció ($t_R$) i la resolució crítica ($R_s$), donant un veredicte sobre si el mètode és "ROBUST" o "POC ROBUST".

## Ús

Per utilitzar el simulador, simplement obre el fitxer `cromatografia4.html` en un navegador web modern (com Google Chrome, Firefox, o Edge). No es requereix cap instal·lació addicional.

## Estructura del Codi

El codi JavaScript està contingut dins del mateix fitxer HTML i ha estat refactoritzat per a una major claredat i mantenibilitat, seguint una arquitectura modular:

- **`appState`:** Un objecte global que centralitza tot l'estat de l'aplicació.
- **Motor de Càlculs:** Funcions pures (`calculateChromatogram`, `calculateKPrime`, `calculatePressure`) que realitzen la lògica científica.
- **Controladors d'Accions:** Funcions que gestionen la lògica de l'aplicació (`startAnalysis`, `runRobustnessTest`).
- **Renderitzat de la UI:** Un conjunt de funcions (`renderUI`, `renderChromatogramSVG`, `renderRobustnessModal`) que generen l'HTML i actualitzen el DOM.
- **Gestió d'Esdeveniments:** La funció `attachEventListeners` assigna els controladors d'esdeveniments als elements de la interfície.
- **Internacionalització (i18n):** Un objecte `translations` conté totes les cadenes de text per a facilitar la traducció a múltiples idiomes.

---
*Desenvolupat per a finalitats educatives. Els models físics són simplificacions i aproximacions dels processos cromatogràfics reals.*