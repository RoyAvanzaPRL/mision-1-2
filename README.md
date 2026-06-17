# mision-2-crud-todo

Pequeña aplicación ToDo creada con Vue 3 y TypeScript. La app permite añadir tareas, marcarlas como hechas, eliminar tareas y conservarlas al recargar la página usando `localStorage`.

## Tecnologías

- Vue 3
- TypeScript
- Vite
- `vue-tsc` para comprobación de tipos

## Dependencias principales

- `vue`: `^3.5.34`
- `vite`: `^8.0.12`
- `typescript`: `~6.0.2`
- `@vitejs/plugin-vue`: `^6.0.6`
- `vue-tsc`: `^3.2.8`
- `@types/node`: `^24.12.3`

## Instalación

Instala las dependencias con pnpm:

```bash
pnpm install
```

Si usas npm, ejecuta:

```bash
npm install
```

## Ejecutar el proyecto

```bash
pnpm dev
```

Después abre la URL que indique Vite, normalmente `http://localhost:5173`.

## Construir para producción

```bash
pnpm build
```

## Previsualizar la build

```bash
pnpm preview
```

## Qué hace el proyecto

- Añade nuevas tareas
- Marca las tareas como hechas
- Elimina tareas
- Guarda las tareas en `localStorage` para que se conserven al recargar la página

## Estructura principal

- `src/App.vue` — estado principal y lógica de tareas
- `src/components/TaskForm.vue` — formulario para crear tareas
- `src/components/TaskList.vue` — lista de tareas
- `src/components/TaskItem.vue` — componente de cada tarea individual
- `src/style.css` — estilos globales
- `src/types.ts` — definición del tipo `Task`