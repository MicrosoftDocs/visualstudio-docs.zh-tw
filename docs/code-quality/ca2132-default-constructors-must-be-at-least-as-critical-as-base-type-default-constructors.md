---
title: CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9602ccd4aae7f3df1a708728203e2ad1c0857776
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176833"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132：預設建構函式至少必須和基底類型的預設建構函式一樣關鍵

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|分類|Microsoft.Security|
|中斷變更|中斷|

> [!NOTE]
> 這個警告只會套用至執行 CoreCLR （CLR 的 Silverlight web 應用程式特定的版本） 的程式碼中。

## <a name="cause"></a>原因

在衍生類別中的預設建構函式的透明度屬性不是重要性不如基底類別的透明度。

## <a name="rule-description"></a>規則描述

型別和成員具有<xref:System.Security.SecurityCriticalAttribute>不可由 Silverlight 應用程式程式碼。 重視安全性的類型以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。 由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。

CoreCLR 平台程式碼，如果基底型別具有公用或保護之不透明的預設建構函式再衍生的型別必須遵守的預設建構函式繼承規則。 衍生的型別也必須擁有預設建構函式，該建構函式必須至少為重要的預設建構函式的基底型別。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此違規情形，請移除類型或不是衍生自安全性不透明的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則的警告。 違反此規則應用程式程式碼將會導致拒絕載入的型別與 CoreCLR <xref:System.TypeLoadException>。

### <a name="code"></a>程式碼

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]