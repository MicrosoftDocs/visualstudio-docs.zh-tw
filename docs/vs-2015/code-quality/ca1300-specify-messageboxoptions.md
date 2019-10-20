---
title: CA1300：指定 MessageBoxOptions |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663612"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300：指定 MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Category|Microsoft。全球化|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 方法會呼叫不接受 <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> 引數之 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 方法的多載。

## <a name="rule-description"></a>規則描述
 若要針對使用由右至左讀取順序的文化特性正確顯示訊息方塊，<xref:System.Windows.Forms.MessageBoxOptions> 列舉的 <xref:System.Windows.Forms.MessageBoxOptions> 和 <xref:System.Windows.Forms.MessageBoxOptions> 成員必須傳遞至 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法。 檢查包含控制項的 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> 屬性，以決定是否要使用由右至左的讀取順序。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請呼叫接受 <xref:System.Windows.Forms.MessageBoxOptions> 引數之 <xref:System.Windows.Forms.MessageBox.Show%2A> 方法的多載。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當程式碼程式庫不會針對使用由右至左讀取順序的文化特性進行當地語系化時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範的方法會顯示訊息方塊，其中包含適用于文化特性讀取順序的選項。 建立範例時，不需要顯示資源檔。 遵循範例中的批註，建立沒有資源檔的範例，並測試由右至左的功能。

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>請參閱
 [桌面應用程式中的 <xref:System.Resources.ResourceManager?displayProperty=fullName> 資源](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
