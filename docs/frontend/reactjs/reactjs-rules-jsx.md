---
title: "Reglas del JSX"
date: "2025-10-12T07:30:17+02:00"
author: "Fco. Javier Cousiño"
categories:
  - "reactjs"
tags:
  - "ReactJS"
  - "JSX"
  - "JavaScript"
description: "Retorna un elemento raíz Para devolver multiples elementos de un componente, envuelvelos en un tag. Puedes usar el tag <div> o el tag <> (Fragment). <> <h1>Hedy Lamarr's Todos</h1> <img src=\"https://i.imgur.com/yXOvdOSs.jpg\" alt=\"Hedy Lamarr\" class=\"photo\" > <ul> ... </ul> </> Cierra todos los tags JSX requiere que los tags sean explicitamente cerrados. Las etiquetas como <img> que no tienen etiquetas de cierre, se deben establecer como <img />. <> <img src=\"https://i.imgur.com/yXOvdOSs.jpg\" alt=\"Hedy Lamarr\" class=\"photo\" /> <ul> <li>Invent new traffic lights</li> <li>Rehearse a movie scene</li> <li>Improve the spectrum technology</li> </ul> </> Usa camelCase JSX se convierte en JavaScript y los atributos escritos se convierten en claves de objetos JavaScript. En sus propios componentes, querrá leer los atributos como variables. Pero JavaScript tiene limitaciones en los nombres de variables, ya que no pueden contener guiones ni ser palabras reservadas como class (en su lugar debes usar className). Es el motivo por el que atributos en React están escritos en camelCase."
---

1. **Retorna un elemento raíz**

Para devolver multiples elementos de un componente, envuelvelos en un tag. Puedes usar el tag `<div>` o el tag `<>` (Fragment).

```
    <>
        <h1>Hedy Lamarr's Todos</h1>
        <img 
            src="https://i.imgur.com/yXOvdOSs.jpg" 
            alt="Hedy Lamarr" 
            class="photo"
        >
        <ul>
            ...
        </ul>
    </>
```

2. **Cierra todos los tags**

JSX requiere que los tags sean explicitamente cerrados. Las etiquetas como `<img>` que no tienen etiquetas de cierre, se deben establecer como `<img />`.

```
    <>
        <img 
            src="https://i.imgur.com/yXOvdOSs.jpg" 
            alt="Hedy Lamarr" 
            class="photo"
        />
        <ul>
            <li>Invent new traffic lights</li>
            <li>Rehearse a movie scene</li>
            <li>Improve the spectrum technology</li>
        </ul>
    </>
```

3. **Usa camelCase**

JSX se convierte en JavaScript y los atributos escritos se convierten en claves de objetos JavaScript. En sus propios componentes, querrá leer los atributos como variables. Pero JavaScript tiene limitaciones en los nombres de variables, ya que no pueden contener guiones ni ser palabras reservadas como `class` (en su lugar debes usar className). Es el motivo por el que atributos en React están escritos en camelCase.

```
    <img 
        src="https://i.imgur.com/yXOvdOSs.jpg" 
        alt="Hedy Lamarr" 
        className="photo"
    />
```

`Por razones historicas, aria-* y data-* están escritos en HTML con guiones.`

### Conversor de HTML a JSX

Existe un conversor gratuito de HTML a JSX en la siguiente [web](https://transform.tools/html-to-jsx)
.
