# [Rubocop](https://github.com/rubocop/rubocop)
RuboCop is a Ruby static code analyzer (a.k.a. linter) and code formatter. Out of the box it will enforce many of the guidelines outlined in the community Ruby Style Guide. Apart from reporting the problems discovered in your code, RuboCop can also automatically fix many of them for you.

RuboCop is extremely flexible and most aspects of its behavior can be tweaked via various configuration options.

## Configure rubocop for rails 
### Needed gems
1. [RuboCop Rails](https://github.com/rubocop-hq/rubocop-rails) 
2. [Rubocop Performance](https://github.com/rubocop/rubocop-performance)

### How to configure rubocop
1. In gemfile please add the following 

```
group :development, :test do 
 # rubocop-rails
 gem 'rubocop-rails', require: false
 # rubocop-performance
 gem 'rubocop-performance', require: false
end
```

2. Run the `bundle install` or `bundle`
3. Create `.rubocop.yml` in the  root directory and put the following code 
```
# AllCops:
#   NewCops: enable
#   Exclude:
#     - 'vendor/**/*'
#     - 'spec/fixtures/**/*'
#     - 'tmp/**/*'
#     - 'bin/bundle'
#   TargetRubyVersion: 3.0.0
#   SuggestExtensions: false

require:
  - rubocop-performance
  - rubocop-rails

AllCops:
  TargetRubyVersion: 3.0.0
  # RuboCop has a bunch of cops enabled by default. This setting tells RuboCop
  # to ignore them, so only the ones explicitly set in this file are enabled.
  DisabledByDefault: true
  Exclude:
    - db/**/*
    - config/**/*
    - bin/**/*
    - vendor/**/*
    - log/**/*
    - tmp/**/*
    - Gemfile
    - Guardfile
    - Rakefile
    - spec/rails_helper.rb
    - spec/spec_helper.rb
    - node_modules/**/*

Performance:
  Exclude:
    - spec/**/*'

Rails:
  Enabled: true

Rails/HttpPositionalArguments:
  Enabled: false

Rails/IndexBy:
  Enabled: true

Rails/IndexWith:
  Enabled: true

Rails/OutputSafety:
  Enabled: true
  Exclude:
    - app/admin/lessons.rb

Rails/UnknownEnv:
  Environments:
    - development
    - test
    - staging
    - production

# Prefer &&/|| over and/or.
Style/AndOr:
  Enabled: true

# Align `when` with `case`.
Layout/CaseIndentation:
  Enabled: true

Layout/ClosingHeredocIndentation:
  Enabled: true

# Align comments with method definitions.
Layout/CommentIndentation:
  Enabled: true

Layout/ElseAlignment:
  Enabled: true

# Align `end` with the matching keyword or starting expression except for
# assignments, where it should be aligned with the LHS.
Layout/EndAlignment:
  Enabled: true
  EnforcedStyleAlignWith: variable
  AutoCorrect: true

Layout/EmptyLineAfterMagicComment:
  Enabled: true

Layout/EmptyLinesAroundAccessModifier:
  Enabled: true
  EnforcedStyle: only_before

Layout/EmptyLinesAroundBlockBody:
  Enabled: true

# In a regular class definition, no empty lines around the body.
Layout/EmptyLinesAroundClassBody:
  Enabled: true

# In a regular method definition, no empty lines around the body.
Layout/EmptyLinesAroundMethodBody:
  Enabled: true

# In a regular module definition, no empty lines around the body.
Layout/EmptyLinesAroundModuleBody:
  Enabled: true

# Use Ruby >= 1.9 syntax for hashes. Prefer { a: :b } over { :a => :b }.
Style/HashSyntax:
  Enabled: true

Layout/FirstArgumentIndentation:
  Enabled: true

# Method definitions after `private` or `protected` isolated calls need one
# extra level of indentation.
Layout/IndentationConsistency:
  Enabled: true
  EnforcedStyle: indented_internal_methods

# Two spaces, no tabs (for indentation).
Layout/IndentationWidth:
  Enabled: true

Layout/LeadingCommentSpace:
  Enabled: true

Layout/SpaceAfterColon:
  Enabled: true

Layout/SpaceAfterComma:
  Enabled: true

Layout/SpaceAfterSemicolon:
  Enabled: true

Layout/SpaceAroundEqualsInParameterDefault:
  Enabled: true

Layout/SpaceAroundKeyword:
  Enabled: true

Layout/SpaceAroundOperators:
  Enabled: true

Layout/SpaceBeforeComma:
  Enabled: true

Layout/SpaceBeforeComment:
  Enabled: true

Layout/SpaceBeforeFirstArg:
  Enabled: true

Style/DefWithParentheses:
  Enabled: true

# Defining a method with parameters needs parentheses.
Style/MethodDefParentheses:
  Enabled: true

Style/FrozenStringLiteralComment:
  Enabled: true
  EnforcedStyle: always
  Exclude:
    - "actionview/test/**/*.builder"
    - "actionview/test/**/*.ruby"
    - "actionpack/test/**/*.builder"
    - "actionpack/test/**/*.ruby"
    - "activestorage/db/migrate/**/*.rb"
    - "activestorage/db/update_migrate/**/*.rb"
    - "actionmailbox/db/migrate/**/*.rb"
    - "actiontext/db/migrate/**/*.rb"

Style/RedundantFreeze:
  Enabled: true

# Use `foo {}` not `foo{}`.
Layout/SpaceBeforeBlockBraces:
  Enabled: true

# Use `foo { bar }` not `foo {bar}`.
Layout/SpaceInsideBlockBraces:
  Enabled: true
  EnforcedStyleForEmptyBraces: space

# Use `{ a: 1 }` not `{a:1}`.
Layout/SpaceInsideHashLiteralBraces:
  Enabled: true

Layout/SpaceInsideParens:
  Enabled: true

# Check quotes usage according to lint rule below.
Style/StringLiterals:
  Enabled: true
  EnforcedStyle: double_quotes

# Detect hard tabs, no hard tabs.
Layout/IndentationStyle:
  Enabled: true

# Empty lines should not have any spaces.
Layout/TrailingEmptyLines:
  Enabled: true

# No trailing whitespace.
Layout/TrailingWhitespace:
  Enabled: true

# Use quotes for string literals when they are enough.
Style/RedundantPercentQ:
  Enabled: true

Lint/AmbiguousOperator:
  Enabled: true

Lint/AmbiguousRegexpLiteral:
  Enabled: true

Lint/ErbNewArguments:
  Enabled: true

# Use my_method(my_arg) not my_method( my_arg ) or my_method my_arg.
Lint/RequireParentheses:
  Enabled: true

Lint/ShadowingOuterLocalVariable:
  Enabled: true

Lint/RedundantStringCoercion:
  Enabled: true

Lint/UriEscapeUnescape:
  Enabled: true

Lint/UselessAssignment:
  Enabled: true

Lint/DeprecatedClassMethods:
  Enabled: true

Style/ParenthesesAroundCondition:
  Enabled: true

Style/HashTransformKeys:
  Enabled: true

Style/HashTransformValues:
  Enabled: true

Style/RedundantBegin:
  Enabled: true

Style/RedundantReturn:
  Enabled: true
  AllowMultipleReturnValues: true

Style/Semicolon:
  Enabled: true
  AllowAsExpressionSeparator: true

# Prefer Foo.method over Foo::method
Style/ColonMethodCall:
  Enabled: true

Style/TrivialAccessors:
  Enabled: true

Performance/FlatMap:
  Enabled: true

Performance/RedundantMerge:
  Enabled: true

Performance/StartWith:
  Enabled: true

Performance/EndWith:
  Enabled: true

Performance/RegexpMatch:
  Enabled: true

Performance/ReverseEach:
  Enabled: true

Performance/UnfreezeString:
  Enabled: true

Performance/DeletePrefix:
  Enabled: true

Performance/DeleteSuffix:
  Enabled: true

Rails/ActiveRecordCallbacksOrder:
  Enabled: true

Rails/AfterCommitOverride:
  Enabled: true

Rails/FindById:
  Enabled: true

Rails/Inquiry:
  Enabled: true

Rails/MailerName:
  Enabled: true

Rails/MatchRoute:
  Enabled: true

Rails/NegateInclude:
  Enabled: true

Rails/Pluck:
  Enabled: true

Rails/PluckInWhere:
  Enabled: true

Rails/RenderInline:
  Enabled: true

Rails/RenderPlainText:
  Enabled: true

Rails/ShortI18n:
  Enabled: true

Rails/SquishedSQLHeredocs:
  Enabled: true

Rails/UniqueValidationWithoutIndex:
  Enabled: false

Rails/WhereExists:
  Enabled: true

Rails/WhereNot:
  Enabled: true

Rails/AttributeDefaultBlockValue:
    Enabled: true
Rails/WhereEquals:
  Enabled: true

```

### How to execute rubocop
1. Go to terminal 
2. Run `bundle exec rubocop` to check code quality