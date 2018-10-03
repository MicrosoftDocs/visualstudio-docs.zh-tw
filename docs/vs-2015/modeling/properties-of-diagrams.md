---
title: 圖表的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 43d5804f1a80b2616e209c47e594b29ad84911a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489828"
---
# <a name="properties-of-diagrams"></a>圖表的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[屬性的圖表](https://docs.microsoft.com/visualstudio/modeling/properties-of-diagrams)。  
  
您可以設定指定如何圖表會顯示在產生的設計工具中的屬性。 例如，您可以指定文字的預設色彩在圖表中。  
  
 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
 下表列出圖表的屬性。  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|填滿色彩|圖表的填滿色彩。|白皮書|  
|文字色彩|在圖表顯示的文字色彩。|黑色|  
|存取修飾詞|類別 （公用或內部） 的存取修飾詞。|Public|  
|自訂屬性|用來將屬性加入至產生的程式碼類別。|\<無 >|  
|產生雙衍生|如果`True`，將產生的基底類別和部分類別 （以支援透過覆寫自訂）。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|  
|具有自訂建構函式|如果`True`，以原始碼提供自訂建構函式。 如需詳細資訊，請參閱 <<c0> [ 覆寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|繼承修飾詞|描述的繼承來源的程式碼類別，產生自圖表的類型 (`none`，`abstract`或`sealed`)。|無|  
|基底的圖表|此圖表的基底類別。|(無)|  
|名稱|此圖表的名稱。|目前的名稱|  
|命名空間|此圖表附屬於命名空間。|目前的命名空間|  
|表示類別|這個圖代表根網域類別。|如果適用於目前的根類別|  
|注意|這個項目相關聯的非正式附註。|\<無 >|  
|會公開為屬性填滿色彩|如果`True`，使用者可以設定產生的設計工具圖表的填滿色彩。 若要將此設定，請在以滑鼠右鍵按一下圖表圖形，然後按一下**新增 Explosed**。|False|  
|公開為屬性的文字色彩|如果`True`，使用者可以設定圖表的文字色彩在產生的設計工具中。 若要將此設定，請在以滑鼠右鍵按一下圖表圖形，然後按一下**新增 Explosed**。|False|  
|描述|描述用來產生的設計工具的文件。|\<無 >|  
|顯示名稱|將會顯示在此圖中產生的設計工具的名稱。|\<無 >|  
|說明關鍵字|用來編製索引的這個圖表 F1 說明關鍵字。|\<無 >|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



