```yml
---
Language: Cpp
AccessModifierOffset: -4
AlignAfterOpenBracket: Align
AlignArrayOfStructures: Right
AlignConsecutiveAssignments:
  Enabled: false
  AcrossEmptyLines: false
  AcrossComments: false
  AlignCompound: false
  PadOperators: false
AlignConsecutiveBitFields:
  Enabled: false
  AcrossEmptyLines: false
  AcrossComments: false
AlignConsecutiveDeclarations:
  Enabled: false
  AcrossEmptyLines: false
  AcrossComments: false
AlignConsecutiveMacros:
  Enabled: true
  AcrossEmptyLines: false
  AcrossComments: false
AlignConsecutiveShortCaseStatements:
  Enabled: true
  AcrossEmptyLines: true
  AcrossComments: true
  AlignCaseColons: false
AlignEscapedNewlines: Right
AlignOperands: Align
AlignTrailingComments:
  Kind: Always
  OverEmptyLines: 1
AllowAllArgumentsOnNextLine: true
AllowAllParametersOfDeclarationOnNextLine: true
AllowShortBlocksOnASingleLine: Never
AllowShortCaseLabelsOnASingleLine: false
AllowShortEnumsOnASingleLine: false
AllowShortFunctionsOnASingleLine: Empty
AllowShortIfStatementsOnASingleLine: Never
AllowShortLambdasOnASingleLine: All
AllowShortLoopsOnASingleLine: false
AlwaysBreakAfterReturnType: None
AlwaysBreakBeforeMultilineStrings: false
AlwaysBreakTemplateDeclarations: Yes
AttributeMacros: []
BinPackArguments: false
BinPackParameters: false
BitFieldColonSpacing: None
BraceWrapping:
  AfterCaseLabel: true
  AfterClass: true
  AfterControlStatement: Always
  AfterEnum: true
  AfterFunction: true
  AfterNamespace: true
  AfterStruct: true
  AfterUnion: true
  AfterExternBlock: true
  BeforeCatch: true
  BeforeElse: true
  BeforeLambdaBody: false
  BeforeWhile: false
  IndentBraces: false
  SplitEmptyFunction: false
  SplitEmptyRecord: true
  SplitEmptyNamespace: true
BreakAfterAttributes: Always
BreakBeforeBinaryOperators: None
BreakBeforeBraces: Custom
BreakBeforeConceptDeclarations: Always
BreakBeforeInlineASMColon: OnlyMultiline
BreakBeforeTernaryOperators: true
BreakConstructorInitializers: BeforeComma
BreakInheritanceList: BeforeComma
BreakStringLiterals: true
ColumnLimit: 80
CompactNamespaces: false
ConstructorInitializerIndentWidth: 4
ContinuationIndentWidth: 4
Cpp11BracedListStyle: true
DeriveLineEnding: true
DerivePointerAlignment: true
EmptyLineAfterAccessModifier: Never
EmptyLineBeforeAccessModifier: LogicalBlock
FixNamespaceComments: true
IncludeBlocks: Merge
IncludeCategories:
  - Regex: '^<'
    Priority: 1
  - Regex: '^"'
    Priority: 2
  - Regex: '.*'
    Priority: 3
IndentAccessModifiers: false
IndentCaseBlocks: true
IndentCaseLabels: false
IndentExternBlock: AfterExternBlock
IndentGotoLabels: true
IndentPPDirectives: BeforeHash
IndentRequiresClause: false
IndentWidth: 4
IndentWrappedFunctionNames: false
InsertBraces: false
InsertNewlineAtEOF: true
KeepEmptyLinesAtEOF: true
KeepEmptyLinesAtTheStartOfBlocks: true
LambdaBodyIndentation: Signature
LineEnding: DeriveLF
MaxEmptyLinesToKeep: 1
NamespaceIndentation: All
PPIndentWidth: -1
PackConstructorInitializers: NextLine
PointerAlignment: Right
ReferenceAlignment: Right
ReflowComments: true
SeparateDefinitionBlocks: Always
ShortNamespaceLines: 1
SortIncludes: CaseInsensitive
SortUsingDeclarations: Lexicographic
SpaceAfterCStyleCast: false
SpaceAfterLogicalNot: false
SpaceAfterTemplateKeyword: false
SpaceAroundPointerQualifiers: Default
SpaceBeforeAssignmentOperators: true
SpaceBeforeCaseColon: false
SpaceBeforeCpp11BracedList: false
SpaceBeforeCtorInitializerColon: true
SpaceBeforeInheritanceColon: true
SpaceBeforeParens: ControlStatements
SpaceBeforeRangeBasedForLoopColon: true
SpaceBeforeSquareBrackets: false
SpaceInEmptyBlock: false
SpaceInEmptyParentheses: false
SpacesBeforeTrailingComments: 1
SpacesInAngles: Never
SpacesInCStyleCastParentheses: false
SpacesInConditionalStatement: false
SpacesInContainerLiterals: false
SpacesInLineCommentPrefix:
  Minimum: 1
  Maximum: 1
SpacesInParens: Never
SpacesInSquareBrackets: false
Standard: Latest
StatementAttributeLikeMacros:
  - Q_EMIT
  - emit
StatementMacros:
  - Q_UNUSED
  - QT_REQUIRE_VERSION
  - Q_CLASSINFO
  - Q_ENUM
  - Q_ENUM_NS
  - Q_FLAG
  - Q_FLAG_NS
  - Q_GADGET
  - Q_GADGET_EXPORT
  - Q_INTERFACES
  - Q_MOC_INCLUDE
  - Q_NAMESPACE
  - Q_NAMESPACE_EXPORT
  - Q_OBJECT
  - Q_PROPERTY
  - Q_REVISION
  - Q_DISABLE_COPY
  - Q_SET_OBJECT_NAME
  - QT_BEGIN_NAMESPACE
  - QT_END_NAMESPACE
  - QML_ADDED_IN_MINOR_VERSION
  - QML_ANONYMOUS
  - QML_ATTACHED
  - QML_DECLARE_TYPE
  - QML_DECLARE_TYPEINFO
  - QML_ELEMENT
  - QML_EXTENDED
  - QML_EXTENDED_NAMESPACE
  - QML_EXTRA_VERSION
  - QML_FOREIGN
  - QML_FOREIGN_NAMESPACE
  - QML_IMPLEMENTS_INTERFACES
  - QML_INTERFACE
  - QML_NAMED_ELEMENT
  - QML_REMOVED_IN_MINOR_VERSION
  - QML_SINGLETON
  - QML_UNAVAILABLE
  - QML_UNCREATABLE
  - QML_VALUE_TYPE
TabWidth: 4
UseTab: Never
WhitespaceSensitiveMacros:
  - STRINGIZE
  - PP_STRINGIZE
  - BOOST_PP_STRINGIZE
  - NS_SWIFT_NAME
  - CF_SWIFT_NAME
...
```

