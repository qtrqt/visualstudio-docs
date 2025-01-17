---
title: "CA1030: Use events where appropriate"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
  - "UseEventsWhereAppropriate"
  - "CA1030"
helpviewer_keywords:
  - "CA1030"
  - "UseEventsWhereAppropriate"
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1030: Use events where appropriate

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Breaking change|Non-breaking|

## Cause

A method name begins with one of the following:

- AddOn
- RemoveOn
- Fire
- Raise

By default, this rule only looks at externally visible methods, but this is [configurable](#configurability).

## Rule description

This rule detects methods that have names that ordinarily would be used for events. Events follow the Observer or Publish-Subscribe design pattern; they are used when a state change in one object must be communicated to other objects. If a method gets called in response to a clearly defined state change, the method should be invoked by an event handler. Objects that call the method should raise events instead of calling the method directly.

Some common examples of events are found in user interface applications where a user action such as clicking a button causes a segment of code to execute. The .NET event model is not limited to user interfaces. It should be used anywhere you must communicate state changes to one or more objects.

## How to fix violations

If the method is called when the state of an object changes, consider changing the design to use the .NET event model.

## When to suppress warnings

Suppress a warning from this rule if the method does not work with the .NET event model.

## Configurability

If you're running this rule from [FxCop analyzers](install-fxcop-analyzers.md) (and not with legacy analysis), you can configure which parts of your codebase to run this rule on, based on their accessibility. For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an .editorconfig file in your project:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

You can configure this option for just this rule, for all rules, or for all rules in this category (Design). For more information, see [Configure FxCop analyzers](configure-fxcop-analyzers.md).
