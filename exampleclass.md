## Diagram Logiki
```mermaid
classDiagram
  class TextTransformer {
    +protected String text;
    +public @NotNull String getText();
    +public abstract @NotNull String transform();
  }
  class TextClass {
    +public TextClass(@NotNull String str);
    @Override
    +public @NotNull String transform();
  }
  TextTransformer <|-- TextClass
```