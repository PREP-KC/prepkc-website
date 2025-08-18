# Technical Details

## Build Tools
- **Sass**: CSS preprocessor for variables, mixins, and organization
- **PostCSS**: CSS post-processor with autoprefixer and minification
- **ImageMin**: Image optimization and WebP conversion
- **ESBuild**: Fast JavaScript bundling and minification
- **Live Server**: Development server with live reload

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
└── package.json        # Dependencies and scripts
```

## Package.json Scripts
```json
{
  "scripts": {
    "dev": "live-server --port=3000 --open=/",
    "build": "npm-run-all build:*",
    "build:css": "sass css/scss/main.scss:dist/css/style.css --style=compressed",
    "build:images": "imagemin img/**/* --out-dir=dist/img",
    "build:js": "esbuild js/main.js --bundle --minify --outfile=dist/js/main.js",
    "watch": "npm-run-all --parallel watch:*"
  }
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

# Image optimization
npm install --save-dev imagemin imagemin-webp imagemin-mozjpeg imagemin-pngquant

# JavaScript tools
npm install --save-dev esbuild terser

# Development tools
npm install --save-dev live-server npm-run-all
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
