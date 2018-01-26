---
title: "屬性的連接埠圖形 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.port
helpviewer_keywords: Domain-Specific Language, port shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8d8059d6399f4bb6e9df988fb5ef24eef9b8f096
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="properties-of-port-shapes"></a>通訊埠圖案的屬性
您可以使用連接埠圖形來表示產生的設計工具中的網域類別。  
  
 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接埠圖形有下表中列出的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|填滿色彩|此圖形的填滿色彩。|白色|  
|填滿漸層停駐模式|此圖形的填滿漸層的模式。|水平|  
|幾何|此圖形 （矩形、 圓角矩形、 橢圓形、 圓形或） 的幾何。|矩形|  
|具有預設的連接點|如果`True`、 圖形將會使用 top，bottom，left 和正確的連接點產生的設計工具中。|False|  
|外框色彩|此圖形外框色彩。|黑色|  
|外框虛線樣式|此圖形 （實線、 虛線、 點、 線、 虛線點點或自訂） 的外框虛線樣式。|實線|  
|外框粗細|此圖形外框粗細。|0.03125|  
|文字色彩|使用此圖形相關聯的文字裝飾色彩。|黑色|  
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個圖形所產生。|\<none>|  
|會產生雙衍生|如果`True`，就會產生 （以支援自訂透過覆寫） 的部分類別和基底類別。 如需詳細資訊，請參閱[覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|具有自訂建構函式|如果`True`，會在原始程式碼中提供的自訂建構函式。 如需詳細資訊，請參閱[覆寫，然後將產生的類別擴充](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述產生通訊埠的來源的程式碼類別的繼承種類 (`none`，`abstract`或`sealed`)。|無|  
|基底連接埠|此圖形的基底類別。|(無)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|此圖形附屬於命名空間。|目前的命名空間|  
|工具提示的類型|如何 （固定，變數，或無） 來定義工具提示。 然後固定的值如果`Fixed Tooltip Text`屬性做為工具提示; 如果變數，然後在工具提示會定義自訂程式碼中。|無|  
|注意|此圖形相關聯的非正式附註。|\<none>|  
|初始高度|此圖形，以英吋的初始高度。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|當做屬性公開的填滿色彩<br /><br /> 公開填滿漸層停駐模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，以滑鼠右鍵按一下圖形定義，然後按一下**新增公開**。|False|  
|描述|用來產生的設計工具的文件。|\<none>|  
|顯示名稱|會產生此圖形設計工具中顯示的名稱。|\<none>|  
|固定的工具提示文字|使用固定的工具提示文字。|\<none>|  
|說明關鍵字|用於檢索這個圖形的 F1 說明關鍵字。|\<none>|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)