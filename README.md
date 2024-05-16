# Description

This is a example of the presentation encompassed to the demonstration of the webR technology

# How-to
This presentation uses revealjs framework inside quarto engine.
Current stable release version of the Quarto doesn't support webr, but
pre-release version 1.42xx works fine.

1. Update or check version of the Quarto.
2. Create new project in RStudio (Quarto web).
3. Install Quarto extension to support webR.
details:  https://github.com/coatless/quarto-webr
4. Create header of a quarto document to setup an output format 
to revealjs presentation and support webR chunks incorporation.
E.g. 
```{markdown}
---
engine: knitr  
format: 
  revealjs:
    incremental: true
webr: 
  show-startup-message: false
filters:
  - webr
---
```

5. Customise the theme of presentation via css.
You can include into the header
```{markdown}
    theme: [dark, custom.scss]
```
7. Customise JS editor vie qwebr-styling.css in an "extension" folder.  
Setup font size and colour, change size of the console output window.

8. Customise JS editor theme via qwebr-monaco-editor-element.js in an "extension" folder.
E.g.
```{js}
require(['vs/editor/editor.main'], function () {
    editor = monaco.editor.create(editorDiv, {
      value: initialCode,
      language: 'r',
      theme: 'vs-dark',
      automaticLayout: true,           // Works wonderfully with RevealJS
      scrollBeyondLastLine: false,
      minimap: {
        enabled: false
      },
      fontSize: '17.5pt',              // Bootstrap is 1 rem
      rules:
        {
          token: "",
          foreground: "ff4500",
          fontStyle: "italic underline",
        },
      renderLineHighlight: "none",     // Disable current line highlighting
      hideCursorInOverviewRuler: true  // Remove cursor indictor in right hand side scroll bar
    });
```

