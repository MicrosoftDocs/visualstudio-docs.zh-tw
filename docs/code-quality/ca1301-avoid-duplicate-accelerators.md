---
title: CA1301：避免使用重複的快速鍵
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1970eefee70fa14179c77566f23f213f09026646
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444390"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301：避免使用重複的快速鍵

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|分類|Microsoft。全球化|
|重大變更|不中斷|

## <a name="cause"></a>原因
型別會擴充 <xref:System.Windows.Forms.Control?displayProperty=fullName>，並包含兩個或多個具有儲存在資源檔中相同存取金鑰的最上層控制項。

## <a name="rule-description"></a>規則描述

存取金鑰也稱為快速鍵，可讓您使用**Alt**鍵來存取控制項的鍵盤。 當多個控制項具有相同的存取金鑰時，不會妥善定義存取金鑰的行為。 使用者可能無法使用存取金鑰來存取所需的控制項，而且可能會啟用非預期的控制項。

此規則的目前執行會忽略功能表項目。 不過，相同子功能表中的功能表項目不應該有相同的存取金鑰。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請為所有控制項定義唯一的存取金鑰。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示的是包含兩個具有相同存取金鑰之控制項的最小表單。 金鑰會儲存在資源檔中，而不會顯示。 不過，它們的值會出現在已加上批註的 `checkBox.Text` 行中。 您可以藉由交換 `checkBox.Text` 行與其批註化的對應專案，來檢查重複快速鍵的行為。 不過，在此情況下，此範例不會從規則產生警告。

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>請參閱

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [桌面應用程式中的資源](/dotnet/framework/resources/index)
