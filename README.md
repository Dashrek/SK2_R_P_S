# SK2_R_P_S
Projekt na przedmiot Sieci Komputerowe 2.  
# Rock Paper Scissors.
---
## Temat: Implementacja gry papier, kamień, nożyce w otoczeniu sieciowym, z dodatkową implementacją umiejętności specjalnych.  
---
### 1. Wybór środowiska, narzędzi i języków oprogramowania.
---

A. Klient:<span style="color: #F9E4B3">Środowiskiem uruchomieniowym [klienta](#client) jest system Windows, ze względu na popularność jego w systemach desktopowych, mnogość bibliotek graficznych, łatwość uruchomienia aplikacji. Narzędziami niezbędnymi zbudowania klienta są [msys2](https://www.msys2.org)- potężny terminal, z mocno rozbudowanym [mingw](https://pl.wikipedia.org/wiki/MinGW), z własnymi kompilatorami i interpreterami języków takich jak python, [golang](https://pl.wikipedia.org/wiki/Go_(język_programowania)), z możliwością dołączania ścieżek i aliasów, za pomocą pliku .bashrc oraz możliwością odpaleniem z tego terminalu narzędzi od jetbrains takich jak: clion i goland. Językiem programowania jest język [go](#golang), który umożliwia korzystanie z łatwej metody łączenia go z językiem C i nieco trudniejszymi metodami dla języków takich jak C++, czy python. Jest to język współbieżny z łatwą implementacją współbieżności, robi zarazem za cmake, lub za skrypty basha.</span>  
B. Serwer:<div class="custom-paragraph">Środowiskiem uruchomieniowym [serwera](#server)</div> jest system linux, ze względu na lepsze biblioteki w języku C
---

```mermaid
classDiagram
  Language_C: +example.c
  Language_C: +example.h
  Objective_File: example.o
  Objective
  Animal <|-- Duck : yellow
  Animal <|-- Fish : green
  Animal <|-- Zebra : blue
  Animal : +int age
  Animal : +String gender
  Animal: +isMammal()
  Animal: +mate()
  class {
    +swim()
    +quack()
  }
  class Fish{
    -sizeInFeet()
    +canEat()
  }
  class Zebra{
    +run()
  }