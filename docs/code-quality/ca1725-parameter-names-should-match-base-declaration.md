---
title: CA1725:參數名稱應該符合基底類型的宣告
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe62c830b7cd3454adbde8b1d3081af11ef1a6b
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841655"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725:參數名稱應該符合基底類型的宣告

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法覆寫中的參數名稱不符合在基底方法宣告參數的名稱或介面宣告的方法中參數的名稱。

根據預設，此規則只會查看外部可見的方法，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，重新命名以符合基底宣告的參數。 修正方法是 COM 可見方法的重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏這項規則，除了先前所提供的程式庫中的 COM 可見方法的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1725.api_surface = private, internal
```

此類別 （命名） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。