# SK2_R_P_S
Projekt na przedmiot Sieci Komputerowe 2.  
# Rock Paper Scissors.
---
## Temat: Implementacja gry papier, kamień, nożyce w otoczeniu sieciowym, z dodatkową implementacją umiejętności specjalnych.  
---
### 1. Wybór środowiska, narzędzi i języków oprogramowania.
---

1. A. Klient:  
Środowiskiem uruchomieniowym [klienta](#client) jest system Windows, ze względu na popularność jego w systemach desktopowych, mnogość bibliotek graficznych, łatwość uruchomienia aplikacji. Narzędziami niezbędnymi zbudowania klienta są [msys2](https://www.msys2.org)- potężny terminal, z mocno rozbudowanym [mingw](https://pl.wikipedia.org/wiki/MinGW), z własnymi kompilatorami i interpreterami języków takich jak python, [golang](https://pl.wikipedia.org/wiki/Go_(język_programowania)), z możliwością dołączania ścieżek i aliasów, za pomocą pliku .bashrc oraz możliwością odpaleniem z tego terminalu narzędzi od jetbrains takich jak: clion i goland. Językiem programowania jest język [go](#golang), który umożliwia korzystanie z łatwej metody łączenia go z językiem C i nieco trudniejszymi metodami dla języków takich jak C++, czy python. Jest to język współbieżny z łatwą implementacją współbieżności, robi zarazem za cmake, lub za skrypty basha. 
1. B. Serwer:  
Środowiskiem uruchomieniowym [serwera](#server) jest system linux, ze względu na lepsze biblioteki w języku C
---

```mermaid
classDiagram
  Language_C: +example.c
  Language_C: +example.h
  Objective_File: example.o
  Go_File: +example.go
  Execute_File: +example.exe

  Language_C -->|gcc -c example.c -o example.o| Objective_File : ""
  Objective_File -->|go build -o example.exe example.go| Execute_File : ""

  Go_File -->|//#cgo LDFLAGS: example.o -lallegro -lallegro_font -lallegro_color -lallegro_primitive| Objective_File : ""
  Go_File -->|'//#include "example.h"'| Objective_File : ""