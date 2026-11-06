---
title: "Status"
date: "2025-10-12T07:30:17+02:00"
author: "Fco. Javier Cousiño"
categories:
  - "github"
tags:
  - "GitHub"
  - "CLI"
description: "gh Status Definición Muestra información la siguiente información sobre GitHub: Incidencias asignadas Pull request asignados Solicitudes de revisión Menciones Actividad del repositorio Argumentos -e, –exclude : lista de los repositorios a excluir en formato propietario/nombre. -o, –org : retorna el estado de la organización. Ejemplos gh status -e cli/cli -e cli/go-gh gh status -o cli"
---

## gh Status

#### Definición

Muestra información la siguiente información sobre GitHub:

- Incidencias asignadas
- Pull request asignados
- Solicitudes de revisión
- Menciones
- Actividad del repositorio

#### Argumentos

-e, –exclude : lista de los repositorios a excluir en formato propietario/nombre.

-o, –org : retorna el estado de la organización.

#### Ejemplos

```
        gh status -e cli/cli -e cli/go-gh
        
        gh status -o cli
```
