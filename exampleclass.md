## Diagram Logiki
```mermaid
classDiagram
  class TextTransformer {
    +protected String text;
    +public @NotNull String getText();
    +public abstract @NotNull String transform();
  }
  class TextClass: TextTransformer {
    +public TextClass(@NotNull String str);
    +public @NotNull String transform();
  }
  TextTransformer <|-- TextClass
```