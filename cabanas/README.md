# RP2 — Cabanas Modulares

Aplicação Astro independente do HTML institucional da RP2 Engenharia. A rota local `/` contém apenas uma página provisória da P1.

## Desenvolvimento local

Requisitos: Node.js >= 22.12.0 e npm.

```powershell
cd cabanas
npm ci
npm run dev
```

Abra http://localhost:4321/.

## Validação

```powershell
npm run check
npm run build
```

O build estático é gerado em `dist/`. Uma publicação futura na Vercel poderá usar `cabanas` como Root Directory. A URL pública e o roteamento serão definidos em etapa posterior.
