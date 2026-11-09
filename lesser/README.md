# Lesser — app

App Android en Expo / React Native. La idea, los modos de fricción y el resto de documentación están en el [README raíz](../README.md).

## Ejecutar

```bash
npm install
npm run android
```

Requiere Node 20+, Android Studio y un build nativo (Expo Go no incluye los módulos de Android).

Para usar un proyecto de Firebase propio o la clave de Gemini:

```bash
cp ../.env.example .env
# rellenar EXPO_PUBLIC_*
```

## Scripts

```bash
npm run start          # servidor de desarrollo de Expo
npm run android        # build y ejecución en Android
npm run lint           # ESLint
npm run build:apk      # APK de debug
npm run build:release-apk
```
