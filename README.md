# makefile_tutorial

Crie um arquivo functions.c com todas as funções necessárias(utilize os includes aqui também)

```
#include <stdio.h>
#include <stdlib.h>

void funcaoX()
{
  printf("Minha função X.\n");
}


```

Crie um arquivo fuctions.h com seus headers.

```
#ifndef _H_FUNCTIONS
#define _H_FUNCTIONS

#define MAX 100

void funcaoX();

#endif
```

Crie um arquivo principal main.c

```
#include <stdio.h>
#include <stdlib.h>
#include "functions.h"

int main()
{
	funcaoX();
	return(0);
}
```

Crie um arquivo Makefile.

```
### Makefile ###
all: functions
functions: functions.o main.o
# O compilador faz a ligação entre os dois objetos
	gcc -o utilizandoMakefile functions.o main.o
#-----> Distancia com o botão TAB ### e não com espaços
functions.o: functions.c
	gcc -o functions.o -c functions.c -W -Wall -pedantic -Wno-implicit
main.o: main.c functions.h
	gcc -o main.o -c main.c -W -Wall -pedantic -Wno-implicit
clean:
	rm -rf *.o
mrproper: clean
	rm -rf functions
```
No exemplo acima, utilizandoMakefile é o nome do executável, basta alterá-lo.

Comandos:

>make clean

Limpará os arquivos .o criados com o make.

>make

Compilará o código-fonte e gerará o executável.

Baseado em:
[Wikibooks/Makefiles](https://pt.wikibooks.org/wiki/Programar_em_C/Makefiles)
