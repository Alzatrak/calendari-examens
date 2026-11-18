# Calendari d'exàmens
Calendari mensual públic per a alumnat, amb edició exclusiva per a dos comptes autoritzats.

## Publicació web
A GitHub, obre **Settings → Pages → Build and deployment → Deploy from a branch** i tria **main / (root)**. El web serà a https://alzatrak.github.io/calendari-examens/

## Configuració necessària de Firebase
GitHub Pages allotja el web però no desa dades. Perquè l'alumnat vegi els exàmens en temps real cal una base de dades Firestore.

1. Crea un projecte a https://console.firebase.google.com.
2. **Project settings → Your apps → Web:** registra l'aplicació i copia els camps públics de `firebaseConfig` al fitxer `index.html`. No afegeixis contrasenyes ni credencials d'administrador.
3. **Firestore Database:** crea la base de dades i substitueix les regles amb el contingut de `firestore.rules` (mai mode prova permanent).
4. **Authentication → Sign-in method:** activa **Email/Password**. Crea manualment només els dos usuaris editors a **Authentication → Users**. No habilitis registre públic.
5. Copia els dos UID de Firebase Authentication i substitueix `UID_PERSONA_1` i `UID_PERSONA_2` **tant** a `index.html` com a `firestore.rules`. Publica les regles al tauler Firebase. La restricció real és a les regles, no a la interfície.
6. Autoritza el domini `alzatrak.github.io` a **Authentication → Settings → Authorized domains**, si cal.

## Verificacions
Comprova lectura en una finestra d'incògnit, i que cadascun dels dos comptes pot crear/editar/esborrar; comprova també que un tercer compte no pot escriure.

**Privacitat:** els esdeveniments són públics; no escriguis dades personals de l'alumnat. La configuració Firebase del navegador és pública per disseny.
