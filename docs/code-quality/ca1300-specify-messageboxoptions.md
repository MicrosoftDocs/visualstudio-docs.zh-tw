---
title: "CA1300： 指定 MessageBoxOptions |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4ce736aa64cba9d66d770f3c4297c1685d690f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300：指定 MessageBoxOptions
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 方法會呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>方法未採用<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>引數。  
  
## <a name="rule-description"></a>規則描述  
 若要顯示訊息方塊是否正確地使用由右至左讀取順序的文化特性為<xref:System.Windows.Forms.MessageBoxOptions>和<xref:System.Windows.Forms.MessageBoxOptions>成員<xref:System.Windows.Forms.MessageBoxOptions>列舉必須傳遞至<xref:System.Windows.Forms.MessageBox.Show%2A>方法。 檢查<xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>來判斷是否要使用由右至左讀取順序包含控制項的屬性。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫的多載<xref:System.Windows.Forms.MessageBox.Show%2A>採用方法<xref:System.Windows.Forms.MessageBoxOptions>引數。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告時不會使用由右至左讀取順序的文化特性的當地語系化程式碼程式庫。  
  
## <a name="example"></a>範例  
 下列範例顯示的選項，適用於不因文化特性的讀取順序的訊息方塊的方法。 資源檔，不會顯示，它才能建置範例。 請依照下列範例不使用資源檔案將範例建置及測試由右至左功能中的註解。  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [桌面應用程式中的資源](/dotnet/framework/resources/index)