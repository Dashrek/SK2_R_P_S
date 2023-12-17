
```mermaid
---
title: Diagram Logiki

---
classDiagram
  class TextTransformer {
    protected String text;
    public @NotNull String getText();
    public abstract @NotNull String transform();
  }
  class TextClass["TextClass : TextTransformer"] {
    +public TextClass(@NotNull String str);
    +public @NotNull String transform();
  }
  class TextTransformerDecorator["TextTransformerDecorator : TextTransformer"] {
    +protected TextTransformer textToTransform;
    +public TextTransformerDecorator(@NotNull TextTransformer textToTransform);
    -public abstract @NotNull String transform();
    +public abstract @NotNull String description();
  }
  class CaseTransform["transform.CaseTransform : TextTransformerDecorator"] {
    +private final Type typeOfTransform;
    +public CaseTransform(@NotNull TextTransformer textToTransform, @NotNull Type typeOfTransform);
    ~public @NotNull String transform();
    ~public @NotNull String description();
    +private @NotNull String caseTransformation(@NotNull String text);
    +public static Type fromName(@NotNull String name);
    enum Type{
      <<Enumeration>>
      UPPER
      LOWER
      CAPITALIZE
      IDENTITY
    }
  }
  TextTransformer <|-- TextTransformerDecorator
  TextTransformer <|-- TextClass
  TextTransformerDecorator <|-- CaseTransform
```