```python
# ==============================================================================
#  _    _            _                     _   _           _             
# | |  | |          | |                   | | | |         | |            
# | |__| | __ _  ___| | ___   _ _ __   ___| |_| |__   ___ | |_ ___  _ __ 
# |  __  |/ _` |/ __| |/ / | | | '_ \ / _ \ __| '_ \ / _ \| __/ _ \| '__|
# | |  | | (_| | (__|   <| |_| | | | |  __/ |_| | | | (_) | || (_) | |   
# |_|  |_|\__,_|\___|_|\_\\__,_|_| |_|\___|\__|_| |_|\___/ \__\___/|_|   
#                                                                        
#                      ╔═╗╔═╗╦  ╔═╗╦ ╦  Retro Hacker Semáforo ╔═╗╔═╗       
#                      ║  ║ ║║  ║ ║║ ║                       ╚═╗╠═╝       
#                      ╚═╝╚═╝╩═╝╚═╝╚═╝                       ╚═╝╩         
# ------------------------------------------------------------------------------
# Asignatura: Lenguajes de Interfaz en TECNM Campus ITT
# Autor(a) : [Mario Leon Gasca]
# Fecha    : 2025/09/24


# ──||  MODO: SYS.OP (OVERRIDE)  ||─────────────────────────────────────────────
#  ▶ Estado: [ RED ]   [ YELLOW ]   [ GREEN ]
#  ▶ Delay configurable: red_ms, yellow_ms, green_ms
#  ▶ Modo debug: led blink + serial dump (logging estilo terminal)
# ------------------------------------------------------------------------------
# «Neo-Grid: Módulo 01 — Señales en la Matriz»  —  Hack the light, learn the time.
# ==============================================================================
```
# Grabación: [Ver en Asciinema](https://asciinema.org/a/EJX1J0WZdZJSGyBp0qDDARwDh)  
# Ensamblador

```assembly
    .data
msg:    .asciz "Número 9 → patrón: 0x7B (gfedcba = 1111011)\n"
len = . - msg

    .text
    .global _start

_start:
    // write(int fd, const void *buf, size_t count)
    mov x8, #64         // syscall number write
    mov x0, #1          // fd = 1 (stdout)
    ldr x1, =msg        // dirección del mensaje
    mov x2, len         // longitud del mensaje
    svc #0              // syscall

    // exit(int status)
    mov x8, #93         // syscall number exit
    mov x0, #0
    svc #0
```
# C#

```csharp
using System;

class Program
{
    static void Main()
    {
        // Segmentos: a, b, c, d, e, f, g
        // Patrón para el número 9 = segmentos a, b, c, f, g encendidos
        // En formato gfedcba: 1111011 (binario) = 0x7B (hex)
        byte pattern = 0x7B;  

        Console.WriteLine("Número 9 → patrón de display:");
        Console.WriteLine($"Hex : 0x{pattern:X2}");
        Console.WriteLine($"Bin : {Convert.ToString(pattern, 2).PadLeft(7, '0')} (gfedcba)");
    }
}
```

