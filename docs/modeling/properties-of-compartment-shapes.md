---
title: "區間圖案的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e87af6c7b95fc05ab7e018f4b9adeb0ea9708868
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-compartment-shapes"></a>區間圖案的屬性
區間圖案是其中一種您可以使用以網域特定語言顯示網域類別的圖形。 您可以展開和摺疊區間。  
  
 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 區間圖案具有下表中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|預設展開摺疊狀態，|如果`Expanded`，建立會顯示的區間。 如果`Collapsed`，它們不是。|展開的|  
|填滿色彩|此圖形的填滿色彩。|白色|  
|填滿漸層停駐模式|此圖形的填滿漸層的模式。|水平|  
|幾何|此圖形 （矩形或圓角矩形） 的幾何。|矩形|  
|具有預設的連接點|如果`True`、 圖形將會使用 top，bottom，left 和正確的連接點產生的設計工具中。|False|  
|會顯示單一區間標頭嗎|如果`False`，圖形具有單一區間，看不到標頭的區間。|True|  
|外框色彩|此圖形外框色彩。|黑色|  
|外框虛線樣式|此圖形，實線、 虛線、 點、 線、 虛線點點 （自訂） 的外框虛線樣式。|實線|  
|外框粗細|此圖形外框粗細。|0.03125|  
|文字色彩|此圖形相關聯的文字裝飾項目使用的色彩。|黑色|  
|存取修飾詞|區間圖案的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別產生的這個區間圖案|\<none>|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述從區間圖案產生來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|  
|基底區間圖案|此圖形的基底類別。|(無)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|此圖形附屬於命名空間。|目前的命名空間|  
|工具提示的型別|如何 （固定，變數，或無） 來定義工具提示。 然後固定的值如果`Fixed Tooltip Text`屬性做為工具提示; 如果變數，然後在工具提示會定義自訂程式碼中。|無|  
|注意|此圖形相關聯的非正式附註。|\<none>|  
|初始高度|此圖形，以英吋的初始高度。 區間圖案，這是只有標頭區段的高度而且無法調整大小。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|當做屬性公開的填滿色彩<br /><br /> 公開填滿漸層停駐模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，以滑鼠右鍵按一下圖形定義，然後按一下**新增公開**。|False|  
|描述|用來產生的設計工具的文件。|\<none>|  
|顯示名稱|會產生此圖形設計工具中顯示的名稱。|\<none>|  
|固定的工具提示文字|使用固定的工具提示文字。|\<none>|  
|說明關鍵字|用於檢索這個圖形的 F1 說明關鍵字。|\<none>|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)