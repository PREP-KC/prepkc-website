# Commands & Operations

## Quick Reference

### Development Commands
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run watch        # Watch for changes
```

### Build Commands
```bash
npm run build:css    # Compile SCSS to CSS
npm run build:images # Optimize images
npm run build:js     # Bundle JavaScript
```

### Code Quality Commands
```bash
npm run lint         # Run all linting checks
npm run format       # Format all code files
npm run quality      # Check linting and formatting
npm run lint:js      # Lint JavaScript files
npm run lint:css     # Lint CSS/SCSS files
npm run lint:html    # Validate HTML files
```

## Setup Commands

### Initial Project Setup
```bash
# Initialize Node.js project
npm init -y

# Install core build tools
npm install --save-dev sass postcss autoprefixer cssnano

# Install image optimization (modern tools)
npm install --save-dev sharp svgo

# Install JavaScript tools
npm install --save-dev esbuild terser

# Install development tools
npm install --save-dev live-server npm-run-all

# Install code quality tools
npm install --save-dev prettier eslint stylelint html-validate

# Install pre-commit hooks
npm install --save-dev husky pre-commit
```

### Configuration Files
```bash
# Create configuration files
touch .prettierrc .eslintrc.js .stylelintrc .pre-commit-config.yaml
```

## Testing Commands

### Code Quality Testing
```bash
# Test all quality checks
npm run quality

# Test individual linting
npm run lint:js
npm run lint:css
npm run lint:html

# Test formatting
npm run format:check
```

### Build Testing
```bash
# Test SCSS compilation
npm run build:css

# Test image optimization
npm run build:images

# Test JavaScript bundling
npm run build:js

# Test full build
npm run build
```

## Development Workflow

### Daily Development
```bash
# Start development server
npm run dev

# Watch for changes
npm run watch

# Check code quality before commit
npm run quality
```

### Before Committing
```bash
# Format all code
npm run format

# Run all linting checks
npm run lint

# Verify everything passes
npm run quality
```

## Troubleshooting Commands

### npm Issues
```bash
# Check npm version
npm --version

# Check Node.js version
node --version

# Clear npm cache
npm cache clean --force

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

### Build Issues
```bash
# Check build output
ls -la dist/

# Check for build errors
npm run build 2>&1 | grep -i error

# Verify file permissions
ls -la css/scss/
```

### Code Quality Issues
```bash
# Fix formatting issues
npm run format

# Check specific file
npx prettier --check filename.html
npx eslint filename.js
npx stylelint filename.scss

# Auto-fix what can be fixed
npx eslint --fix filename.js
npx stylelint --fix filename.scss
```

## Performance Testing

### Lighthouse Testing
```bash
# Install Lighthouse globally
npm install -g lighthouse

# Run Lighthouse audit
lighthouse https://localhost:3000 --output=json --output-path=./lighthouse-report.json

# Run with specific settings
lighthouse https://localhost:3000 --only-categories=performance,accessibility
```

### Core Web Vitals
```bash
# Test page load performance
npm run build
# Then test with browser dev tools or PageSpeed Insights
```

## Deployment Commands

### Local Testing
```bash
# Build for production
npm run build

# Test production build locally
npx serve dist/

# Check production files
ls -la dist/
du -sh dist/
```

### File Management
```bash
# Check file sizes
du -sh img/* | sort -hr
du -sh css/* | sort -hr

# Find large files
find . -type f -size +1M -exec ls -lh {} \;

# Check image optimization
ls -la img/ | grep -E "\.(jpg|jpeg|png|webp)$"
```

## Git Commands

### Pre-commit Setup
```bash
# Install pre-commit hooks
pre-commit install

# Run pre-commit on all files
pre-commit run --all-files

# Update pre-commit hooks
pre-commit autoupdate
```

### Quality Gates
```bash
# Pre-commit will automatically run:
# - Code formatting (Prettier)
# - JavaScript linting (ESLint)
# - CSS/SCSS linting (Stylelint)
# - HTML validation
# - File size checks
# - YAML validation
```

## Environment Setup

### Windows PowerShell
```powershell
# Fix execution policy (run as Administrator)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Test npm
npm --version
```

### macOS/Linux
```bash
# Check Node.js installation
which node
which npm

# Set up environment variables if needed
export PATH="$PATH:$(npm bin -g)"
```

## Quick Checks

### System Health
```bash
# Check all tools are working
node --version && npm --version && sass --version

# Check build tools
npx sass --version
npx postcss --version
npx imagemin --version
```

### Project Status
```bash
# Check what's installed
npm list --depth=0

# Check for outdated packages
npm outdated

# Check for security issues
npm audit
```
