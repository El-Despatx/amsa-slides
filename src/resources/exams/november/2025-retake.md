---
format: html
---

1) De quina comanda de linux forma part aquest codi? (0.7 punts)

```c
//...
  ok = (setpriority (PRIO_PROCESS, 0, current_niceness + adjustment) == 0);
//...
  execvp (argv[i], &argv[i]);
//...
```

2) Suposant un procés amb PID 324, digues quina comanda de les que hem vist a classe usaries per a comunicar-t'hi/controlar aquest procés, explica quins son els arguments que rep la comanda i per a que serveixen. (0.7 punts)

3) Un cop un sysadmin ha creat i activat correctament un swapfile, escriu el següent programa amb C amb l’objectiu de consumir memòria de manera progressiva: (1.2 punts)

```c
#include <stdio.h>
#include <unistd.h>
#include <string.h>
#include <stdlib.h>
#include <stdbool.h>

const size_t BLOCK_SIZE = 600 * 1024 * 1024;

int main(int argc, char **argv) {
    void *my_memory_pointer;

    while (true) {
        my_memory_pointer = malloc(BLOCK_SIZE);
        memset(my_memory_pointer, 0, BLOCK_SIZE);
        sleep(2);
    }
    return 0;
}
```

Després d’un cert temps d’execució, el programa acaba amb el següent error:

```bash
core dumped with SIGSEGV (11)
```

Per què es produeix aquest error? Com es podria evitar o solucionar?


4) Digues si es verdader o fals: (0.9 punts) [+0.15p per cada resposta correcta, -0.10p per cada error]

    1. Un `tmpfs` pot usar memòria SWAP i se li pot limitar la mida màxima,
    mentre que a un `ramfs` no.
    2. Les `syscalls` son la forma que té el kernel d'usar serveis de userspace.
    3. Pujar-li el `nice` a un procés requreix sudo mentre que baixar-li no.
    4. El permís d'execió en un directori permet que s'hi pugui entrar.
    5. Les dades emmagatzemades en un `tmpfs` no sobreviuen després d'un reboot.
    6. La comanda per enviar la senyal `SIGTERM` a un procés es `send -TERM <pid>`.