# React: Hooks y State Management

React Hooks revolucionaron la forma en que escribimos componentes. Descubre cómo usarlos en tus proyectos.

## 📌 Resumen

- **Dificultad**: Intermedio
- **Tiempo de lectura**: 12 minutos
- **Versión de React**: 16.8+

## ¿Qué son los Hooks?

Los Hooks son funciones que te permiten "enganchar" el estado y otras características de React en componentes funcionales.

### Hooks básicos

#### useState
```javascript
import { useState } from 'react';

function Contador() {
  const [contador, setContador] = useState(0);
  
  return (
    <div>
      <p>Contador: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </div>
  );
}
```

#### useEffect
```javascript
import { useEffect, useState } from 'react';

function Articulos() {
  const [articulos, setArticulos] = useState([]);
  
  useEffect(() => {
    // Este código se ejecuta después del renderizado
    fetch('/api/articulos')
      .then(res => res.json())
      .then(data => setArticulos(data));
  }, []); // Array vacío = solo al montar
  
  return (
    <ul>
      {articulos.map(art => <li key={art.id}>{art.titulo}</li>)}
    </ul>
  );
}
```

## State Management

### Context API (Integrado)
```javascript
import { createContext, useContext, useState } from 'react';

const TemaContext = createContext();

export function TemaProvider({ children }) {
  const [tema, setTema] = useState('claro');
  
  return (
    <TemaContext.Provider value={{ tema, setTema }}>
      {children}
    </TemaContext.Provider>
  );
}

function MiComponente() {
  const { tema, setTema } = useContext(TemaContext);
  
  return (
    <button onClick={() => setTema(tema === 'claro' ? 'oscuro' : 'claro')}>
      Tema actual: {tema}
    </button>
  );
}
```

### Redux (Para aplicaciones grandes)
```javascript
import { createSlice, configureStore } from '@reduxjs/toolkit';
import { useDispatch, useSelector } from 'react-redux';

const articulosSlice = createSlice({
  name: 'articulos',
  initialState: [],
  reducers: {
    agregarArticulo: (state, action) => {
      state.push(action.payload);
    }
  }
});

const store = configureStore({
  reducer: {
    articulos: articulosSlice.reducer
  }
});

function MiComponente() {
  const articulos = useSelector(state => state.articulos);
  const dispatch = useDispatch();
  
  return (
    <button onClick={() => dispatch(articulosSlice.actions.agregarArticulo({}))}>
      Agregar artículo
    </button>
  );
}
```

## Hooks personalizados

```javascript
function useFormulario(inicial) {
  const [valores, setValores] = useState(inicial);
  
  const manejarCambio = (e) => {
    const { name, value } = e.target;
    setValores({ ...valores, [name]: value });
  };
  
  const resetear = () => setValores(inicial);
  
  return { valores, manejarCambio, resetear };
}

// Uso
function Formulario() {
  const { valores, manejarCambio, resetear } = useFormulario({ 
    nombre: '', 
    email: '' 
  });
  
  return (
    <form>
      <input 
        name="nombre" 
        value={valores.nombre} 
        onChange={manejarCambio}
      />
      <button type="button" onClick={resetear}>Limpiar</button>
    </form>
  );
}
```

## Mejores prácticas

!!! warning "Importante"
    - Solo llama Hooks en el nivel superior (no en bucles o condicionales)
    - Solo llama Hooks desde componentes funcionales
    - Usa linters para evitar errores

## Conclusión

Los Hooks han hecho que React sea más poderoso y accesible. Domina estos conceptos y escribirás componentes más limpios y mantenibles.

---

**Recursos útiles:**
- [Documentación oficial de Hooks](https://react.dev/reference/react)
- [React Query](https://tanstack.com/query/)
- [Zustand - State Management ligero](https://github.com/pmndrs/zustand)
