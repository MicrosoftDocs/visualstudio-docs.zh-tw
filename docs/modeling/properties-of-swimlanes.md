---
title: "屬性的泳道 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.swimlane
helpviewer_keywords: Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84107514e728dbfa79b7dfdaee6c3febaee21274
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-swimlanes"></a>泳道的屬性
您可以加入圖表的泳道。 泳道分成垂直或水平區域的圖表。 您可以定義其他的圖形會顯示在泳道內部。 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 泳道具有下表中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|主體填滿色彩|主體的泳道填滿色彩。|白色|  
|標頭填滿色彩|標頭的泳道填滿色彩。|暗灰色|  
|分隔符號色彩|分隔線的色彩。|LightGray|  
|分隔符號的線條樣式|分隔線的樣式 (`Solid`， `Dash`， `Dot`， `DashDot`， `DashDotDot`，或`Custom`)。|`Dash`|  
|分隔符號寬度|以英吋的分隔線的粗細。|0.03125|  
|文字色彩|使用此泳道相關聯的文字裝飾色彩。|黑色|  
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至程式碼從這個泳道產生的類別。|\<none>|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述從泳道產生來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|  
|基底的泳道|此泳道基底類別。|(無)|  
|名稱|此泳道的名稱。|目前的名稱|  
|命名空間|具有此泳道附屬於命名空間。|目前的命名空間|  
|工具提示的型別|定義工具提示的方式 (`fixed`， `variable`，或`none`)。 如果`fixed`的值`Fixed Tooltip Text`屬性用; 如果`variable`，則會在自訂程式碼中定義工具提示。|\<none>|  
|注意|與這個泳道相關聯的非正式附註。|\<none>|  
|對齊|水平或垂直對齊方式。|垂直|  
|初始高度|此英吋的泳道，初始的高度。 僅適用於水平的泳道。|0|  
|初始寬度|此英吋的泳道，初始的寬度。 僅適用於垂直泳道。|0|  
|公開文字色彩|如果`True`，使用者可以設定在產生的設計工具的泳道的色彩。 若要設定這種情況，以滑鼠右鍵按一下 「 泳道 」 圖形，然後按一下**新增公開**。|False|  
|描述|用來產生的設計工具的文件。|\<none>|  
|顯示名稱|將參考此泳道類別產生的設計工具中顯示的名稱。|\<none>|  
|固定的工具提示文字|使用固定的工具提示文字。|\<none>|  
|說明關鍵字|用於檢索這個泳道的 F1 說明關鍵字。|\<none>|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)