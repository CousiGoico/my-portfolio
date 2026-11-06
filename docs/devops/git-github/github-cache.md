---
title: "Cache"
date: "2025-10-12T07:30:17+02:00"
author: "Fco. Javier Cousiño"
categories:
  - "github"
tags:
  - "GitHub"
  - "CLI"
  - "Cache"
description: "Trabaja con las caches de Github Actions. gh cache delete Definición Elimina las caches de Github Actions Sintaxis gh cache delete [| | –all] [flags] Argumentos -a, –all: elimina todas las caches. -R, –repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO. Ejemplos gh cache delete 1234 // By id gh cache delete cache-key // By cache-key gh cache delete 1234 --repo cli/cli gh cache delete --all gh cache list Definición Lista las caches de Github Actions."
---

Trabaja con las caches de Github Actions.

## gh cache delete

#### Definición

Elimina las caches de Github Actions

#### Sintaxis

gh cache delete [|  | –all] [flags]

#### Argumentos

-a, –all: elimina todas las caches.

-R, –repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

#### Ejemplos

```
    gh cache delete 1234 // By id

    gh cache delete cache-key // By cache-key

    gh cache delete 1234 --repo cli/cli

    gh cache delete --all
```

## gh cache list

#### Definición

Lista las caches de Github Actions.

#### Sintaxis

```
    gh cache list [flags]
```

#### Argumentos

-L, –limit : número máximo de caches para buscar.

-O, –order : orden de caches a retornar: {asc|desc}.

-S, –sort : ordena la busqueda de caches: {created\_at|last\_accessed\_at|size\_in\_bytes}.

-R, –repo <[HOST/]OWNER/REPO>: selecciona otro repositorio usando el formato [HOST/]OWNER/REPO.

#### Ejemplos

```
    gh cache list

    gh cache list --repo cli/cli

    gh cache list --sort last_accessed_at --order asc
```
