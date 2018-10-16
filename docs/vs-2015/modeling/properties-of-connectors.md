---
title: 接點的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b78858b14674eafeb044b168a8bb8927af9f5769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171843"
---
# <a name="properties-of-connectors"></a>接點的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

連接器會代表產生的設計工具中的網域關聯性。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 連接器有下列表格中所列的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|色彩|此連接器的色彩。|黑色|  
|虛線樣式|此連接器 （實線、 虛線、 點、 線、 虛線點點或自訂） 的列虛線樣式。|實線|  
|來源端樣式|（HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或無） 此接點來源端樣式。|無|  
|目標端樣式|（HollowArrow、 EmptyArrow、 FilledArrow、 EmptyDiamond、 FilledDiamond，或無） 此接點目標端樣式。|無|  
|文字色彩|使用此連接器與相關聯的文字裝飾項目的色彩。|黑色|  
|Thickness|這個連接器的線條的粗細，單位為英吋。|0.03125|  
|存取修飾詞|類別的存取層級 (`public`或`internal`)。|Public|  
|自訂屬性|用來將屬性加入至來源的程式碼類別，產生來自此連接器。|\<無 >|  
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|繼承修飾詞|描述從連接器會產生來源的程式碼類別繼承的類型 (`none`，`abstract`或`sealed`)。|無|  
|基底接點|此接點的基底類別。|(無)|  
|名稱|此連接器的名稱。|目前的名稱|  
|命名空間|此連接器附屬於命名空間。|目前的命名空間|  
|工具提示類型|（固定、 變數或 none） 」 來定義 「 工具提示的方式。 如果固定，則值`Fixed Tooltip Text`屬性做為工具提示; 若變數，然後工具提示中定義的自訂程式碼。|\<無 >|  
|注意|此連接器與相關聯的非正式附註。|\<無 >|  
|路徑樣式|用於路由接點的樣式。 A`Rectilinear`連接器可讓直角會視需要;`Straight`連接器不會執行。|直線形|  
|公開為屬性的色彩<br /><br /> 當做屬性公開的虛線樣式<br /><br /> 公開為屬性的粗細<br /><br /> 公開 （expose) 的文字色彩|如果`True`，使用者可以設定圖形的所述的屬性。 若要設定這種情況，請以滑鼠右鍵按一下圖形定義，然後按一下**加入已公開**。|False|  
|描述|用來產生的設計工具的文件。|\<無 >|  
|顯示名稱|將會顯示在產生的設計工具，此連接器的名稱。|\<無 >|  
|固定的工具提示文字|用於固定工具提示文字。|\<無 >|  
|說明關鍵字|用來編製索引的這個項目 F1 說明關鍵字。|\<無 >|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



