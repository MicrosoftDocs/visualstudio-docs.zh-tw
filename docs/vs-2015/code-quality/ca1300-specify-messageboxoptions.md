---
title: CA1300： 指定 MessageBoxOptions |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf2cf17b41248032caf01b0cfedbe9b70ecbefb2
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588402"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300：指定 MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1300： 指定 MessageBoxOptions](https://docs.microsoft.com/visualstudio/code-quality/ca1300-specify-messageboxoptions)。

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|分類|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因
 方法會呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>方法不接受<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引數。

## <a name="rule-description"></a>規則描述
 若要顯示訊息方塊，正確的使用由右至左讀取順序的文化特性<xref:System.Windows.Forms.MessageBoxOptions>並<xref:System.Windows.Forms.MessageBoxOptions>的成員<xref:System.Windows.Forms.MessageBoxOptions>列舉型別必須傳遞給<xref:System.Windows.Forms.MessageBox.Show%2A>方法。 檢查<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>來判斷是否要使用由右至左讀取順序，包含控制項的屬性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A>採用方法<xref:System.Windows.Forms.MessageBoxOptions>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告時不會使用由右至左讀取順序的文化特性當地語系化程式碼程式庫。

## <a name="example"></a>範例
 下列範例會顯示訊息方塊具有適當的文化特性的讀取順序選項的方法。 資源檔，不會顯示，它才能建置範例。 請依照下列範例中，若要建置沒有資源檔範例，並測試從右至左功能中的註解。

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [桌面應用程式中的資源](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



