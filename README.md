# maquina-sencilla
Emulador sencillo de una hipotética máquina con 256 bytes de memoria, sin registros, con 4 instrucciones (`ADD`, `JMP`, `CMP` y `BEQ`) y una sola flag
`FZ`.

Se ha creado con fines educativos, tanto para mí como para quien pueda leer el código, ya que en su mayoría es muy legible y fácil de entender (`src/components.zig`).

## Instrucciones de uso
- Descargar el emulador de [Releases](https://github.com/susoferreira/maquina-sencilla/releases) o usar la versión [web](https://susoferreira.github.io/emu/emu.html).
- El ejecutable tiene _docking_ activado, lo que significa que las ventanas se pueden acoplar entre ellas como prefiera el usuario.
- El programa de ejemplo que viene precargado demuestra como funciona la sintaxis del assembler, usando `label :`, `*breakpoint :` y `;comentario`.
- En el menu se pueden ver las opciones que ofrece el programa: Guardar y cargar archivos (texto plano), exportar a .ms (versión de msdos de la maquina sencilla) y generar diagrama. tambien las opciones de ejecucción del código (ensamblar, ejecutar instruccion...).

### Generación de diagramas
Los diagramas se generan analizando las instrucciones y usando mermaid. El resultado inicial no es perfecto pero es fácilmente modificable al editar el html o su código en un editor de mermaid.

### Avanzado 
- El inspector de variables internas de la máquina permite modificar su estado, aunque modificar algunas de estas variables (como `ALU_ENABLE_A` la mayoría del tiempo no afectará a la ejecución, porque son inmediatamente sobreescritas según el estado de `UC_INTERNAL_STATE`).

## Compilar
1. Instalar [Zig](https://ziglang.org/) (**versión 0.15.2**).
2. Ejecutar `zig build run`.
3. Mirar la documentación de zig para compilar a otros targets.

> [!WARNING]
> Es importante clonar el repositorio con submodulos incluidos:
>
> `git clone --recurse-submodules https://github.com/susoferreira/maquina-sencilla`
>
> o
>
> `git clone --recurse-submodules git@github.com:susoferreira/maquina-sencilla.git`

### Web
- Instalar emsdk en la raíz del proyecto.
- Ejecutar `./build_web.sh`.
- Para lanzar la web **se necesita** un servidor web. Se puede usar `./emsdk/upstream/emscripten/emrun ./zig-out/web/emu.html`.

## Librerías utilizadas
- [Sokol](https://github.com/floooh/sokol) (Graphics Backend).
- [cimgui](https://github.com/cimgui/cimgui) (GUI).
- [nfd-zig](https://github.com/fabioarnold/nfd-zig) (File Dialogs).
- [ImGuiColorTextEdit](https://github.com/BalazsJako/ImGuiColorTextEdit) (Text editor).
- [Imgui Club](https://github.com/ocornut/imgui_club) (Hex Editor).
