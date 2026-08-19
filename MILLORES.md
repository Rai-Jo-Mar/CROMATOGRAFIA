# Possibles Millores per al Simulador HPLC

Aquest document recull una llista de possibles millores i noves funcionalitats que es podrien afegir al simulador HPLC per fer-lo encara més potent i didàctic.

## Millores en el Model Científic

1.  **Efecte de la Mida de Partícula ($d_p$):**
    - Afegir un paràmetre per seleccionar la mida de partícula de la fase estacionària (p. ex., 5 µm, 3.5 µm, 1.8 µm).
    - Això hauria d'afectar directament:
        - **L'eficiència (N):** L'eficiència és inversament proporcional a la mida de partícula ($N \propto 1/d_p$). Pics més estrets amb partícules més petites.
        - **La pressió (P):** La pressió és inversament proporcional al quadrat de la mida de partícula ($P \propto 1/d_p^2$). Permetria simular la diferència entre HPLC i UHPLC.

2.  **Efecte del Diàmetre Intern de la Columna ($d_c$):**
    - Afegir un paràmetre per al diàmetre de la columna (p. ex., 4.6 mm, 2.1 mm).
    - Afectaria el temps mort ($t_0$) i la sensibilitat (pics més alts en columnes més estretes per al mateix volum d'injecció).

3.  **Model de Resolució Més Avançat:**
    - Implementar l'equació de Purnell completa per a la resolució, que depèn de l'eficiència (N), selectivitat ($\alpha$) i retenció (k').
    - Això permetria visualitzar millor com cada paràmetre contribueix a la separació.

4.  **Simulació de Soroll i Deriva de la Línia Base:**
    - Afegir un soroll de fons aleatori al cromatograma per a un aspecte més realista.
    - Simular una deriva de la línia base, especialment durant els gradients.

## Millores en la Interfície i Experiència d'Usuari (UI/UX)

1.  **Integració Manual de Pics:**
    - Permetre a l'usuari fer clic i arrossegar sobre la línia base per "integrar" manualment un pic.
    - El simulador calcularia l'àrea del pic seleccionat i la mostraria.

2.  **Superposició de Cromatogrames:**
    - Afegir una funció per "congelar" un cromatograma actual i superposar-lo amb un de nou després de canviar els paràmetres. Això facilitaria la comparació directa dels efectes.

3.  **Mòdul de Desenvolupament de Mètodes Guiat:**
    - Crear un mode "tutorial" on el simulador proposa un problema (p. ex., "separa aquests dos pics coeluïts") i guia l'usuari a través dels passos lògics per optimitzar el mètode.

4.  **Quantificació a partir de la Corba de Calibració:**
    - Després de generar una corba de calibració, permetre la injecció d'una "mostra problema" amb una concentració desconeguda.
    - El simulador hauria de mesurar l'alçada del pic i utilitzar l'equació de la recta per calcular i mostrar la concentració de l'analit a la mostra problema.

## Millores Tècniques

1.  **Separació del Codi:**
    - Tot i que la versió actual és un sol fitxer per portabilitat, es podria dividir en mòduls JavaScript (`.js`) separats (p. ex., `ui.js`, `engine.js`, `state.js`) i utilitzar un empaquetador com Webpack o Vite per al desenvolupament. Això milloraria l'organització per a projectes més grans.

2.  **Optimització del Renderitzat:**
    - En lloc de re-renderitzar tot l'HTML amb `innerHTML`, es podria implementar un sistema de "diffing" del DOM més eficient, on només s'actualitzen els nodes que realment canvien. Això milloraria el rendiment i evitaria la pèrdua de focus en els camps d'entrada.