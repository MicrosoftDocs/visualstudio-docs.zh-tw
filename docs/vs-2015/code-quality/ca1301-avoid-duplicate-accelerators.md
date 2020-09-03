---
title: CA1301：避免重複的快速鍵 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 772c9bee3f43c42701bfa460c622f4a225ec59cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539174"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301:避免使用重複的快速鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|類別|Microsoft。全球化|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型會延伸 <xref:System.Windows.Forms.Control?displayProperty=fullName> 並包含兩個以上的最上層控制項，這些控制項具有儲存在資源檔中的相同存取金鑰。

## <a name="rule-description"></a>規則描述
 便捷鍵也稱為快速鍵，可讓鍵盤使用 ALT 鍵存取控制項。 當多個控制項具有重複的便捷鍵時，就無法妥善定義便捷鍵的行為。 使用者可能無法存取所需的控制項，方法是使用存取金鑰，以及要啟用的控制項以外的控制項。

 此規則的目前執行會忽略功能表項目。 不過，相同子功能表中的功能表項目不應具有相同的存取金鑰。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請定義所有控制項的唯一存取金鑰。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示最基本的表單，其中包含兩個具有相同存取金鑰的控制項。 金鑰會儲存在資源檔中，而不會顯示;不過，它們的值會出現在已加上批註的 `checkBox.Text` 行中。 您可以藉由將行與批註的對應專案交換，來檢查重複快速鍵的行為 `checkBox.Text` 。 不過，在此情況下，此範例不會產生規則的警告。

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Resources.ResourceManager?displayProperty=fullName>[桌面應用程式中的資源](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
