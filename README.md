# Práctica Git

Este repositorio está dedicado a la práctica y aprendizaje de Git, incluyendo alias útiles y comandos avanzados como `rebase interactivo`, `squash`, entre otros.

---

## Configuración de Alias en Git

Los alias en Git permiten crear accesos rápidos a comandos largos o complejos, facilitando su uso y mejorando la productividad.

### Alias para `git log` - `git lg`

Este alias mejora la visualización del historial de commits, mostrando un grafo compacto y coloreado.

#### Configuración:

```sh
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```

#### Explicación:

- `--graph`: Muestra una representación visual del historial de commits en forma de árbol.
- `--abbrev-commit`: Muestra solo los primeros caracteres del hash del commit.
- `--decorate`: Incluye referencias (ramas, etiquetas) en la salida.
- `--format`: Personaliza la salida, incluyendo colores, tiempos relativos y autores.
- `--all`: Muestra todas las ramas.

### Alias para `git status` - `git s`

Muestra un resumen del estado del repositorio en un formato compacto.

#### Configuración:

```sh
git config --global alias.s "status -sb"
```

#### Explicación:

- `-s`: Muestra el estado en una forma corta.
- `-b`: Indica en qué rama estamos actualmente.

---

## Comandos Avanzados en Git

### Rebase Interactivo (`git rebase -i`)

El rebase interactivo permite modificar la historia de commits, combinando, reordenando o eliminando commits.

#### Uso:

```sh
git rebase -i HEAD~N
```

Donde `N` es la cantidad de commits recientes que quieres modificar.

#### Opciones dentro del rebase interactivo:

- `pick`: Mantiene el commit tal como está.
- `reword`: Permite cambiar el mensaje del commit.
- `edit`: Permite modificar el commit (agregar o eliminar cambios).
- `squash` (s): Combina este commit con el anterior y permite cambiar el mensaje.
- `fixup` (f): Combina este commit con el anterior sin modificar el mensaje.
- `drop`: Elimina el commit.

#### Ejemplo:

```
pick 123abc Primer commit
squash 456def Segundo commit (se fusionará con el anterior)
pick 789ghi Tercer commit
```

Esto fusionará el commit `456def` con `123abc`, permitiendo modificar el mensaje resultante.

### Restablecer cambios (`git reset` vs `git revert`)

- `git reset`: Borra commits de la historia (solo en local si ya fueron empujados).
- `git reset --soft HEAD~1`: Revierte el último commit, manteniendo los cambios en el staging.
- `git reset --hard HEAD~1`: Revierte el último commit y elimina los cambios.
- `git revert HEAD`: Crea un nuevo commit que revierte el último cambio, sin eliminar el historial.

### Deshacer cambios en archivos (`git checkout`, `git restore`)

- `git restore archivo.txt`: Revierte los cambios no confirmados en el archivo.
- `git checkout -b nueva-rama`: Crea y cambia a una nueva rama.

### Stashing (`git stash`)

Permite guardar temporalmente cambios sin comprometerlos.

- `git stash`: Guarda cambios sin confirmarlos.
- `git stash pop`: Recupera los cambios almacenados en el stash.
- `git stash list`: Muestra las entradas en el stash.

---

## Conclusión

Estos alias y comandos avanzados mejoran la eficiencia en el uso de Git. La práctica constante con `rebase`, `stash`, y `reset` ayuda a comprender mejor la gestión del historial en los proyectos.

