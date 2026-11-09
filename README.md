<p align="center">
  <img src="lesser/assets/images/icon.png" alt="Lesser" width="96" />
</p>

<h1 align="center">Lesser</h1>

<p align="center">
  App Android para reducir el tiempo de pantalla degradando la experiencia de uso en vez de bloquear aplicaciones.<br/>
  Proyecto del <strong>Impacthon 2026</strong> (ETSE, USC).
</p>

## La idea

Los bloqueos duros funcionan al principio, pero la frustración de no poder abrir una app termina en desinstalación. Lesser no impide abrir nada: deja que uses el móvil, pero la experiencia empeora de forma progresiva cuanto más tiempo pasas. La decisión de parar es del usuario.

La fricción se aplica con APIs nativas de Android (volumen, VPN local, filtros de pantalla y cámara), sin root, y se divide en tres niveles.

## Modos

### Soft

- **Silencios aleatorios.** Cada 3–5 minutos de uso, el audio multimedia se corta entre 20 y 40 segundos. Se activa a partir de un umbral de uso.
- **"Wifi malo".** Una VPN local añade latencia solo a las apps que más enganchan (Instagram, TikTok, X, Facebook, Snapchat, Reddit y YouTube). El retardo sube de 200 ms a 4 s a lo largo de una hora de sesión: el contenido sigue cargando, pero cada vez tarda más.

### Mid

- Todo lo de Soft.
- **Parpadeo de pantalla.**
- **Monocromo progresivo.** Un filtro reduce la saturación de la pantalla a medida que acumulas uso, hasta dejarla en blanco y negro.

### Hardcore

- Todo lo de Mid.
- **Selfie sin aviso.** Hace una foto en un momento aleatorio para pillarte en una mala postura.
- **Launcher minimalista.** Pendiente.

## Resto de la app

- **Estadísticas reales** vía `UsageStatsManager`: tiempo de pantalla, apps más usadas, mapa de calor tipo GitHub, rachas y objetivo diario.
- **Social**: sigue a amigos, feed de actividad y ranking por percentil.
- **Lista blanca** para excluir apps necesarias (mensajería, mapas, banca...).
- **Mensajes con Gemini** generados a partir de tus estadísticas.
- **Firebase**: Auth, Firestore, Realtime Database y Functions (limpieza de datos al borrar la cuenta).
- **Español e inglés**, tema claro/oscuro.

## Stack

Expo 54 · React Native 0.81 · TypeScript · Firebase · Kotlin/Java para los módulos nativos.

## Ejecutar

Requisitos: Node 20+, Android Studio y un proyecto de Firebase.

```bash
git clone https://github.com/fabiomode2/Lesser.git
cd Lesser/lesser
npm install
npm run android
```

La app trae una configuración pública de Firebase por defecto. Para usar otro proyecto o la clave de Gemini, copia el `.env.example` a `lesser/.env` y rellena los valores.

Hace falta un build nativo: Expo Go no incluye el módulo de estadísticas de uso ni las APIs de fricción.

Desplegar backend:

```bash
cd backend
firebase deploy --only firestore,functions
```

## Estructura

```text
lesser/                App Expo / React Native
├── app/               Pantallas (Expo Router)
├── components/        UI: inicio, social y ajustes
├── services/          Firebase, uso, ajustes y tareas en segundo plano
├── modules/           Módulo nativo de estadísticas de uso
└── android/           Proyecto Android
backend/               Reglas, índices y Cloud Functions
```

## Estado

Prototipo de hackathon, no un producto terminado. En `main` funcionan las cuentas, las estadísticas, el social y los ajustes. Las medidas de fricción están implementadas de forma parcial y repartidas entre `main` y ramas sin fusionar (`leer-tiempos`, `Monocromo`, `background-task-fab`). El launcher minimalista no está hecho.
