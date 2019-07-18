---
title: 通訊埠圖案的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69ec18362f596633fa508f1f842db027e59a616b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701537"
---
# <a name="properties-of-port-shapes"></a>通訊埠圖案的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用連接埠圖形來表示產生的設計工具中的網域類別。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接埠圖形具有下表中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|填滿色彩|此圖形的填滿色彩。|白皮書|  
|填滿漸層模式|此圖形的填滿漸層停駐的模式。|水平|  
|幾何|此圖形 （矩形、 圓角矩形、 橢圓形或圓形） 的幾何。|矩形|  
|有預設的連接點|如果`True`、 圖形會使用上、 下、 左和右連接點產生的設計工具中。|False|  
|外框色彩|此圖形的外框色彩。|黑色|  
|外框虛線樣式|（實線、 虛線、 點、 線、 虛線點點或自訂），此圖形的外框虛線樣式。|實線|  
|外框粗細|此圖形的外框粗細。|0.03125|  
|文字色彩|使用此圖形相關聯的文字裝飾項目的色彩。|黑色|  
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別從這個圖形產生。|\<無>|  
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱[覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述的產生從連接埠之來源的程式碼類別繼承的類型 (`none`，`abstract`或`sealed`)。|none|  
|基底連接埠|此圖形的基底類別。|(無)|  
|名稱|此圖形的名稱。|目前的名稱|  
|命名空間|此圖形附屬於命名空間。|目前的命名空間|  
|工具提示類型|（固定、 變數或 none） 」 來定義 「 工具提示的方式。 如果固定，則值`Fixed Tooltip Text`屬性做為工具提示; 若變數，然後工具提示中定義的自訂程式碼。|none|  
|注意|此圖形相關聯的非正式附註。|\<無>|  
|初始的高度|此圖形，以英吋的初始高度。|1|  
|初始寬度|此圖形，以英吋的初始寬度。|1.5|  
|當做屬性公開的填滿色彩<br /><br /> 公開的填滿漸層模式<br /><br /> 公開為屬性的 外框色彩<br /><br /> 公開為屬性的 外框虛線樣式<br /><br /> 公開為屬性的外框粗細<br /><br /> 公開 （expose) 的文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，請以滑鼠右鍵按一下圖形定義，然後按一下**加入已公開**。|False|  
|描述|用來產生的設計工具的文件。|\<無>|  
|顯示名稱|將會顯示在產生的設計工具，此圖形的名稱。|\<無>|  
|固定的工具提示文字|用於固定工具提示文字。|\<無>|  
|說明關鍵字|用來編製索引為此圖形的 F1 說明關鍵字。|\<無>|  
  
## <a name="see-also"></a>另請參閱  
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
