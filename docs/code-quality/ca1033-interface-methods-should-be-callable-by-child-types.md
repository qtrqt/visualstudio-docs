---
title: "CA1033: Interface methods should be callable by child types"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "InterfaceMethodsShouldBeCallableByChildTypes"
  - "CA1033"
helpviewer_keywords:
  - "CA1033"
  - "InterfaceMethodsShouldBeCallableByChildTypes"
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1033: Interface methods should be callable by child types

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Category|Microsoft.Design|
|Breaking change|Non-breaking|

## Cause
An unsealed externally visible type provides an explicit method implementation of a public interface and does not provide an alternative externally visible method that has the same name.

## Rule description
Consider a base type that explicitly implements a public interface method. A type that derives from the base type can access the inherited interface method only through a reference to the current instance (`this` in C#) that is cast to the interface. If the derived type reimplements (explicitly) the inherited interface method, the base implementation can no longer be accessed. The call through the current instance reference will invoke the derived implementation; this causes recursion and an eventual stack overflow.

This rule does not report a violation for an explicit implementation of <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> when an externally visible `Close()` or `System.IDisposable.Dispose(Boolean)` method is provided.

## How to fix violations
To fix a violation of this rule, implement a new method that exposes the same functionality and is visible to derived types or change to a nonexplicit implementation. If a breaking change is acceptable, an alternative is to make the type sealed.

## When to suppress warnings
It is safe to suppress a warning from this rule if an externally visible method is provided that has the same functionality but a different name than the explicitly implemented method.

## Example
The following example shows a type, `ViolatingBase`, that violates the rule and a type, `FixedBase`, that shows a fix for the violation.

[!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]

## See also
[Interfaces](/dotnet/csharp/programming-guide/interfaces/index)