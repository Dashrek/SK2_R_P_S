##Diagram Logiki
```mermaid
classDiagram
  class TextTransformer {
    +protected String text;
    +public @NotNull String getText();
    +public abstract @NotNull String transform();
  }
```