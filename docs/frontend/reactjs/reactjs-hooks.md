---
title: "React JS - Hooks"
date: "2025-10-12T07:30:17+02:00"
author: "Fco. Javier Cousiño"
categories:
  - "reactjs"
tags:
  - "ReactJS"
  - "JavaScript"
  - "Hooks"
description: "HOOKS Los hooks son funcionalidades integradas en REACT JS que te ayudan y te facilitan el desarrollo de la aplicación. HOOK DE ESTADO Permite almacenar la información de la entrada de un usuario en memoria. Un caso de uso sería el almacenamiento de la información del usuario que ha iniciado sesión, o el identificador de un elemento seleccionado en un listado. useState: administra una variable de estado que puedes actualizar directamente."
---

## HOOKS

Los [hooks](https://es.react.dev/reference/react)
son funcionalidades integradas en **REACT JS** que te ayudan y te facilitan el desarrollo de la aplicación.

#### **HOOK DE ESTADO**

Permite almacenar la información de la entrada de un usuario en memoria. Un caso de uso sería el almacenamiento de la información del usuario que ha iniciado sesión, o el identificador de un elemento seleccionado en un listado.

- **useState**: administra una variable de estado que puedes actualizar directamente.
- **useReducer**: administra una variable de estado cuya actualización se gestiona mediante una función reductora.

  ```
    function ImageGallery() {
        const [index, setIndex] = useState(0);
    // ...
  ```

#### **HOOK DE CONTEXTO**

Permite compartir información a los componentes hijos sin la necesidad de pasar dicha información como props. Un ejemplo de uso de este hook sería compartir el tema de la aplicación o la configuración del usuario entre los diferentes componentes hijos.

- **useContext**: lee y se suscribe a un contexto.

  ```
    function Button() {
        const theme = useContext(ThemeContext);
    // ...
  ```

#### **HOOK DE REFS**

Mantiene informacion que no es usada para renderizar. Son útiles cuando necesitas trabajar con sistemas distintos de React, como las APIs integradas del navegador. El id de un timeout sería un ejemplo de dato para almacenar en este tipo de hook.

`Este tipo de hook no vuelve a renderizar tu componente. En el caso del uso del hook de estado si se renderiza el componente.`

- **useRef**: administra una referencia, como por ejemplo un nodo del DOM.
- **useImperativeHandle**: permite personalizar la *ref* expuesta por tu componente. Esto rara vez se usa.

  ```
    function Form() {
        const inputRef = useRef(null);
    // ...
  ```

#### **HOOK DE EFECTO**

Se usa para conectarse y sincronizarse con sistemas externos (red, DOM del navegador, animaciones, widgets, …).

`No uses este tipo de hooks para guiar el flujo de datos de tu aplicación.`

- **useEffect**: permite a un componente conectarse con un sistema externo.
- **useLayoutEffect**: (variación poco usado de useEffect) se activa antes de que el navegador vuelva a pintar la pantalla. Se suelen hacer cálculos de maquetación (layout).
- **useInsertionEffect**: (variación poco usado de useEffect) se activa antes de que React haga cambios en el DOM. Aquí las bibliotecas pueden insertar CSS dinámico.

  ```
    function ChatRoom({ roomId }) {
        useEffect(() => {
            const connection = createConnection(roomId);
            connection.connect();
            return () => connection.disconnect();
        }, [roomId]);
    // ...
  ```

#### **HOOK DE RENDIMIENTO**

Permite realizar un renderizado cacheado si los datos no han sido cambiado desde el renderizado anterior. Puedes separar las actualizaciones del renderizado haciendo que actualizaciones bloqueantes sean síncronas para mejorar el rendimiento.

- **useMemo**: permite guardar en caché los resultados de un cálculo costoso.
- **useCallback**: permite guardar en caché una función definida antes de pasarl a un componente optimizado.
- **useTransition**: marca una transición de estado como no bloqueante para permitir que otras actualizaciones la interrumpan.
- **UseDeferredValue**: aplaza la actualización de una parte no crítica de la interfaz de usuario y deja que otras partes se actualicen primero.

  ```
    function TodoList({ todos, tab, theme }) {
        const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
        // ...
    }
  ```

#### **OTROS HOOKS**

Otros hooks interesantes de conocer.

- **useDebugValue**: personaliza la etiqueta en las Herramientas de Desarrollo de React muestra para el Hook personalizado.
- **useId**: permite que un componente se asocie a un ID único. Normalmente se asocia a las APIs de accesibilidad.
- **useSyncExternalStore**: suscribe un componente a un almacenamiento externo.
