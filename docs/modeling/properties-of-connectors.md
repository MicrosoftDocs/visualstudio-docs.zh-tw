---
title: "屬性的連接器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 858ce6fd3d53cd580a2aaac1b6b5c160dffac517
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-connectors"></a>接點的屬性
連接器代表產生的設計工具中的網域關聯性。  
  
 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接器有下列表格中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|色彩|此連接器的色彩。|黑色|  
|虛線樣式|此連接器 （實線、 虛線、 點、 線、 虛線點點或自訂） 線條的虛線樣式。|實線|  
|來源端樣式|此連接器 （HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或 None） 來源結束樣式。|無|  
|目標的結束樣式|此連接器 （HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或 None） 目標結束樣式。|無|  
|文字色彩|使用此連接器相關聯的文字裝飾色彩。|黑色|  
|Thickness|此連接器，以英吋表示線條的粗細。|0.03125|  
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至產生來自此連接器的來源的程式碼類別。|\<none>|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述產生從連接器的來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|  
|基底的連接器|此連接器基底類別。|(無)|  
|名稱|此連接器的名稱。|目前的名稱|  
|命名空間|此連接器附屬於命名空間。|目前的命名空間|  
|工具提示的型別|如何 （固定，變數，或無） 來定義工具提示。 然後固定的值如果`Fixed Tooltip Text`屬性做為工具提示; 如果變數，然後在工具提示會定義自訂程式碼中。|\<none>|  
|注意|此連接器相關聯的非正式附註。|\<none>|  
|路徑樣式|用於路由連接器的樣式。 A`Rectilinear`連接器可做為必要項; 直角開啟`Straight`連接器並不會。|直線|  
|公開為屬性的色彩<br /><br /> 當做屬性公開的虛線樣式<br /><br /> 公開為屬性的粗細<br /><br /> 公開文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，以滑鼠右鍵按一下圖形定義，然後按一下**新增公開**。|False|  
|描述|用來產生的設計工具的文件。|\<none>|  
|顯示名稱|將此連接器產生的設計工具中顯示的名稱。|\<none>|  
|固定的工具提示文字|使用固定的工具提示文字。|\<none>|  
|說明關鍵字|用來編製索引的這個項目 F1 說明關鍵字。|\<none>|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)