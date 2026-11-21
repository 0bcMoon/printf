# _printf

A small C implementation of formatted output using variadic arguments. The public entry point is declared in `main.h`:

```c
int _printf(const char *format, ...);
```

The formatter dispatches `%s`, `%c`, `%d`, `%i`, `%%`, `%b`, and `%u`. It is a learning implementation with a limited format set.

## Build

Requires a C compiler and a POSIX environment with `write`. The repository has no `main` function, so compiling every source directly into an executable requires a separate driver.

To compile the implementation into object files:

```sh
gcc -Wall -pedantic -Werror -Wextra -std=gnu89 -c _printf.c _put_thing.c leet_print.c outils.c
```

For a small executable, create `example.c`:

```c
#include "main.h"

int main(void)
{
    _printf("Hello, %s! %d %%\n", "world", 42);
    return (0);
}
```

Then compile and run it:

```sh
gcc -Wall -pedantic -Werror -Wextra -std=gnu89 example.c _printf.c _put_thing.c leet_print.c outils.c -o printf-example
./printf-example
```

## Layout

- `_printf.c`: format parsing and variadic argument handling.
- `leet_print.c`: conversion dispatch.
- `_put_thing.c` and `outils.c`: output and conversion helpers.
- `main.h`: function declarations.
