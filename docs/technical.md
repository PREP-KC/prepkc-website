# Technical Details

## Build Tools
- **Sass**: CSS preprocessor for variables, mixins, and organization
- **PostCSS**: CSS post-processor with autoprefixer and minification
- **Sharp**: Modern image optimization and WebP conversion
- **SVGO**: SVG optimization and compression
- **ESBuild**: Fast JavaScript bundling and minification
- **Live Server**: Development server with live reload

## Code Quality & Linting Tools
- **Prettier**: Code formatting for HTML, CSS, and JavaScript
- **ESLint**: JavaScript linting and code quality
- **Stylelint**: CSS/SCSS linting and best practices
- **HTML-validate**: HTML validation and accessibility checking
- **Pre-commit hooks**: Automated quality checks before commits
- **Husky**: Git hooks management for pre-commit automation

## Project Structure
```
prepkc-website/
├── css/
│   ├── scss/           # Source SCSS files
│   │   ├── base/       # Variables, reset, typography
│   │   ├── components/ # Buttons, cards, navigation
│   │   ├── layout/     # Header, footer, grid
│   │   └── pages/      # Page-specific styles
│   └── style.css       # Compiled CSS output
├── dist/               # Build output folder
├── img/                # Source images
├── scripts/            # Build automation scripts
├── .prettierrc         # Prettier configuration
├── .eslintrc.js        # ESLint configuration
├── .stylelintrc        # Stylelint configuration
├── .pre-commit-config.yaml # Pre-commit hooks
└── package.json        # Dependencies and scripts
```

## Package.json Scripts (Complete)
```json
{
  "scripts": {
    "dev": "live-server --port=3000 --open=/",
    "build": "npm-run-all build:*",
    "build:css": "sass css/scss/main.scss:dist/css/style.css --style=compressed",
    "build:images": "node scripts/optimize-images.js",
    "build:js": "esbuild js/main.js --bundle --minify --outfile=dist/js/main.js",
    "watch": "npm-run-all --parallel watch:*",
    "lint": "npm-run-all lint:*",
    "lint:js": "eslint js/**/*.js",
    "lint:css": "stylelint 'css/**/*.scss'",
    "lint:html": "html-validate **/*.html",
    "format": "prettier --write '**/*.{html,css,scss,js}'",
    "format:check": "prettier --check '**/*.{html,css,scss,js}'",
    "quality": "npm run lint && npm run format:check"
  }
}
```

## Pre-commit Configuration
```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files

  - repo: https://github.com/pre-commit/mirrors-prettier
    rev: v3.0.0
    hooks:
      - id: prettier
        types: [file]
        types_or: [html, css, scss, javascript]

  - repo: https://github.com/pre-commit/mirrors-eslint
    rev: v8.45.0
    hooks:
      - id: eslint
        files: \.(js)$
        types: [file]

  - repo: https://github.com/stylelint/pre-commit
    rev: v15.7.0
    hooks:
      - id: stylelint
        files: \.(css|scss)$
        types: [file]
```

## Linting Configurations

### ESLint Configuration
```javascript
// .eslintrc.js
module.exports = {
  env: {
    browser: true,
    es2021: true,
    node: true
  },
  extends: [
    'eslint:recommended'
  ],
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module'
  },
  rules: {
    'no-unused-vars': 'warn',
    'no-console': 'warn',
    'prefer-const': 'error'
  }
}
```

### Stylelint Configuration
```json
// .stylelintrc
{
  "extends": "stylelint-config-standard-scss",
  "rules": {
    "selector-class-pattern": null,
    "scss/at-rule-no-unknown": true,
    "scss/selector-no-redundant-nesting-selector": true
  }
}
```

### Prettier Configuration
```json
// .prettierrc
{
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "es5",
  "bracketSpacing": true,
  "htmlWhitespaceSensitivity": "css",
  "endOfLine": "lf"
}
```

## PostCSS Configuration
```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('autoprefixer'),
    require('cssnano')({
      preset: ['default', {
        discardComments: { removeAll: true },
        normalizeWhitespace: true,
        colormin: true
      }]
    })
  ]
}
```

## SCSS Structure
```scss
// css/scss/main.scss
@import 'base/variables';
@import 'base/reset';
@import 'base/typography';
@import 'components/buttons';
@import 'components/cards';
@import 'components/navigation';
@import 'layout/header';
@import 'layout/footer';
@import 'pages/home';
@import 'pages/about';
```

## Dependencies to Install
```bash
# Core build tools
npm install --save-dev sass postcss autoprefixer cssnano

# Image optimization (modern tools)
npm install --save-dev sharp svgo

# JavaScript tools
npm install --save-dev esbuild terser

# Development tools
npm install --save-dev live-server npm-run-all

# Code quality tools
npm install --save-dev prettier eslint stylelint html-validate

# Pre-commit hooks
npm install --save-dev husky pre-commit
```

## Browser Support
- **Modern browsers**: Full feature support
- **Older browsers**: Graceful degradation
- **Mobile**: Touch-optimized navigation
- **Accessibility**: WCAG 2.1 AA compliance

## Performance Targets
- **CSS**: <30KB (40% reduction)
- **Images**: <800KB (60% reduction)
- **JavaScript**: <50KB bundled
- **First Paint**: <1.5s
- **Lighthouse Score**: >90
