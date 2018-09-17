---
title: CA1301：避免使用重複的快速鍵
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4dac6beddf43e88d47a54ddf2b0e0d56e387038
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547199"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301：避免使用重複的快速鍵

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|類別|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 型別擴充<xref:System.Windows.Forms.Control?displayProperty=fullName>和包含兩個或多個具有相同的存取金鑰儲存在資源檔中的最上層控制項。

## <a name="rule-description"></a>規則描述

存取金鑰，也稱為快速鍵，可讓鍵盤存取控制項使用**Alt**索引鍵。 當多個控制項都有相同的存取金鑰時，不妥善定義便捷鍵的行為。 使用者可能無法使用便捷鍵，以存取適用的控制項，並不是一個控制項可能會啟用。

目前的實作，此規則會忽略功能表項目。 不過，在相同的子功能表的功能表項目不應有相同的存取金鑰。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，定義所有控制項的唯一存取的金鑰。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示最基本的表單，其中包含兩個具有相同的存取金鑰的控制項。 金鑰會儲存在資源檔，不會顯示它。 不過，其值會出現在已標成註解`checkBox.Text`行。 可檢查重複的快速鍵的行為，藉由交換`checkBox.Text`行與其標成註解的對應項目。 不過，在此情況下，此範例不會產生警告的規則。

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [桌面應用程式中的資源](/dotnet/framework/resources/index)