---
title: "CA1307: Specify StringComparison"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords:
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1307: Specify StringComparison

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Category|Microsoft.Globalization|
|Breaking change|Non-breaking|

## Cause
A string comparison operation uses a method overload that does not set a <xref:System.StringComparison> parameter.

## Rule description
Many string operations, most important the <xref:System.String.Compare%2A> and <xref:System.String.Equals%2A> methods, provide an overload that accepts a <xref:System.StringComparison> enumeration value as a parameter.

Whenever an overload exists that takes a <xref:System.StringComparison> parameter, it should be used instead of an overload that does not take this parameter. By explicitly setting this parameter, your code is often made clearer and easier to maintain.

## How to fix violations
To fix a violation of this rule, change string comparison methods to overloads that accept the <xref:System.StringComparison> enumeration as a parameter. For example: change `String.Compare(str1, str2)` to `String.Compare(str1, str2, StringComparison.Ordinal)`.

## When to suppress warnings
It is safe to suppress a warning from this rule when the library or application is intended for a limited local audience and will therefore not be localized.

## See also

- [Globalization Warnings](../code-quality/globalization-warnings.md)
- [CA1309: Use ordinal StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)