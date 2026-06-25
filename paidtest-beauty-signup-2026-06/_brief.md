# Brief · paidtest-beauty-signup-2026-06

- **Mode:** paid-test (sign-up landing para tráfico de paid media)
- **Vertical:** beauty
- **Goal:** crear cuenta (SSO Google + email passwordless) → trial 14 días
- **Variable testeada:** mensaje del hero (H1+sub) — CTA constante
- **Variantes (message-match al aviso):**
  - `a` agenda/DM: "Llená tu agenda sin vivir contestando el DM."
  - `b` señas/ausencias: "Cobrá la seña antes del turno."
  - `c` página propia: "Tu página de turnos tan profesional como tu trabajo."
- **Form:** Google + email only (password en paso posterior — passwordless step 1)
- **Proof:** carrusel de mockups MOBILE de storefronts beauty reales, con auto-rotación (proof + product demo). Usernames provistos por JP.
- **Instrumentación:** captura utm_* + v; pass-through a app.agora.red/signup; eventos signup_cta_click / signup_google_click (Amplitude si está cargado — a confirmar wiring/keys).
- **Stats:** sin números por ahora (no inventar).
- **Reference:** mejora de la pantalla de sign-up actual de Flash (captura JP).
- **Modules:** mockup (Path A, screenshot real, $0) + animation (rotación, $0). No paid modules.

## Mejoras vs. captura actual (lo que se está probando)
1. Un solo H1 dominante (eliminar el "Creá tu página" que competía).
2. Form a 1 campo + Google (passwordless paso 1) — menos fricción.
3. CTA alto contraste (--frost-primary + --sh-glow) vs. lavanda lavado.
4. Risk-reducer pegado al CTA.
5. Fondo plano sobrio, sin gradientes/lavados.
6. Proof real (carrusel storefronts) en vez de stats sin verificar.
7. paid-test: hero por variante + message-match + instrumentación.

## Caveat
Mostrar storefronts de clientes reales es uso outward-facing — OK para test/prototipo; pedir permiso antes de publicar externamente.
