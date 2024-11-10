## React + TypeScript + Vite
Este template configura um ambiente mínimo para iniciar projetos com React, TypeScript e Vite, incluindo suporte a Hot Module Replacement (HMR) e algumas regras do ESLint.

## Plugins disponíveis
Atualmente, dois plugins oficiais estão disponíveis para integração com React:

* @vitejs/plugin-react: Utiliza Babel para Fast Refresh.
* @vitejs/plugin-react-swc: Utiliza SWC para Fast Refresh, proporcionando maior desempenho em projetos maiores.

## Configuração aprimorada do ESLint
Para aplicações em produção, é recomendável configurar o ESLint com regras de verificação de tipo para um código mais robusto:

# Defina as opções do parser no nível superior de parserOptions da seguinte forma:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

1. Substitua tseslint.configs.recommended por tseslint.configs.recommendedTypeChecked ou tseslint.configs.strictTypeChecked para regras de verificação de tipo mais rigorosas.

2. Opcionalmente, adicione ...tseslint.configs.stylisticTypeChecked para regras estilísticas adicionais.

3. Instale o plugin eslint-plugin-react e atualize a configuração:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Set the react version
  settings: { react: { version: '18.3' } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
