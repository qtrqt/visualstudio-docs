---
title: "CA1505: Avoid unmaintainable code"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "AvoidUnmaintainableCode"
  - "CA1505"
helpviewer_keywords:
  - "AvoidUnmaintainableCode"
  - "CA1505"
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1505: Avoid unmaintainable code

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Category|Microsoft.Maintainability|
|Breaking change|Non-breaking|

## Cause

A type or method has a low maintainability index value.

## Rule description

The maintainability index is calculated by using the following metrics: lines of code, program volume, and cyclomatic complexity. Program volume is a measure of the difficulty of understanding of a type or method that's based on the number of operators and operands in the code. Cyclomatic complexity is a measure of the structural complexity of the type or method. You can learn more about code metrics at [Measure complexity and maintainability of managed code](../code-quality/code-metrics-values.md).

A low maintainability index indicates that a type or method is probably difficult to maintain and would be a good candidate to redesign.

## How to fix violations

To fix this violation, redesign the type or method and try to split it into smaller and more focused types or methods.

## When to suppress warnings

You can suppress this warning when the type or method cannot be split or is considered maintainable despite its large size.

## See also

- [Maintainability warnings](../code-quality/maintainability-warnings.md)
- [Measure complexity and maintainability of managed code](../code-quality/code-metrics-values.md)