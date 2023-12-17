#### pl.put.poznan.transformer.server.logic
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
    ~public @NotNull String transform();
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
    +public enum Type;
}
class Enum["public enum Type"]{
    +public static Type fromName(@NotNull String name);
    <<enumeration>>
    UPPER
    LOWER
    CAPITALIZE
    IDENTITY
}
class DuplicatesRemovalTransform["transform.DuplicatesRemovalTransform : TextTransformerDecorator"] {
  +private final boolean removeAllow;
  +public DuplicatesRemovalTransform(@NotNull TextTransformer textToTransform, boolean removingAllowed);
  ~public @NotNull String transform();
  ~public @NotNull String description();
  +private @NotNull String removeAdjacentDuplicates(@NotNull String input);
}
class LaTeXEscapesTransform["transform.LaTeXEscapesTransform : TextTransformerDecorator"]{
  +private static final Map<Character, String> latexCharacterMappings;
  +private final boolean latexCharactersAllowed;
  +public LaTeXEscapesTransform(@NotNull TextTransformer textToTransform, boolean latexCharactersAllowed);
  ~public @NotNull String transform();
  ~public @NotNull String description();
  +private @NotNull String addLaTeXEscapes();
}
class NumberExpansionTransform["NumberExpansionTransform : TextTransformerDecorator"]{
  +private static final Map<Integer, String> DIGITS;
  +private static final Map<Integer, String> TEENS;
  +private static final Map<Integer, String> TENS;
  +private static final Map<Integer, String> HUNDREDS;
  +private static final PluralVariant thousands;
  +private static final PluralVariant millions;
  +private static final PluralVariant billions;
  +private static final PluralVariant trillions;
  +private static final PluralVariant quadrillions;
  +private static final PluralVariant quintillions;
  +private final boolean numberExpandAllowed;
  +public NumberExpansionTransform(@NotNull TextTransformer textToTransform, boolean numberExpandAllowed);
  +private static @NotNull String numberInWords(long number);
  ~public @NotNull String transform();
  ~public @NotNull String description();
  +private @NotNull String expandNumbers(@NotNull String s);
}
class ReverseTransform["ReverseTransform : TextTransformerDecorator"]{
  +private final boolean inverseAllow;
  +public ReverseTransform(@NotNull TextTransformer textToTransform, boolean reversalAllowed);
  ~public @NotNull String transform();
  ~public @NotNull String description();
  +private @NotNull String revertString(@NotNull String input);
}
class ShortcutTransform["ShortcutTransform : TextTransformerDecorator"]{
  +private final Type shortcutType;
  +private final Map<String, String> shortcutMap;
  +public ShortcutTransform(@NotNull TextTransformer textToTransform, @NotNull Type shortcutType);
  +private Map<String, String> initializeShortcutMap();
  ~public @NotNull String transform();
  ~public @NotNull String description();
  +public @NotNull String applyShortcutModification(@NotNull String inputText);
  +public enum Type;
}
class Enum1["public enum Type"]{
    +public static Type fromName(@NotNull String name);
    <<enumeration>>
    EXPAND
    COMPRESS
}

  ShortcutTransform .. Enum1
  TextTransformerDecorator <|-- ShortcutTransform
  TextTransformerDecorator <|-- ReverseTransform
  TextTransformerDecorator <|-- NumberExpansionTransform
  TextTransformerDecorator <|-- LaTeXEscapesTransform
  TextTransformerDecorator <|-- DuplicatesRemovalTransform
  CaseTransform .. Enum
  TextTransformer <|-- TextTransformerDecorator
  TextTransformer <|-- TextClass
  TextTransformerDecorator <|-- CaseTransform
```