# DWC-lite
Simplified wrapper for Duet Web Control. Mainly distinguished by the absence of unnecessary functionality for many printers, the logistics of traveling through the tabs have been changed.
The shell was optimized and created for the PRESTO 3D printer.

Sorry for the messy code.

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

In order to use the local development setup with software versions >= 3.2.0, it is possible to add `M586 C"*"` to your `config.g`.
However, this is a potential security issue because it permits cross-origin requests from ALL foreign sites.

### Compiles and minifies for production

```
npm run build
```
