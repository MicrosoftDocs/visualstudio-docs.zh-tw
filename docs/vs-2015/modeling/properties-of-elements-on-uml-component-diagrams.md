---
title: 在 UML 元件圖上項目的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb99ea1efb070c3e79b294bd5d06eedf131623f0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790080"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>UML 元件圖中的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 元件圖中，圖表上的每個項目都會有屬性。 若要查看項目的屬性，以滑鼠右鍵按一下的項目在圖表上或在**UML 模型總管**，然後按一下**屬性**。 屬性會出現在**屬性**視窗。  
  
> [!NOTE]
>  本主題有關 UML 元件圖中的項目屬性。 如需如何閱讀 UML 元件圖的詳細資訊，請參閱[UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)。 如需如何繪製 UML 元件圖的詳細資訊，請參閱[UML 元件圖： 方針](../modeling/uml-component-diagrams-guidelines.md)。  
  
## <a name="properties-of-elements"></a>項目屬性  
  
|屬性|預設|項目|描述|  
|--------------|-------------|-------------|-----------------|  
|**名稱**|預設名稱|全部|識別項目。|  
|**限定的名稱**|命名空間 :: 名稱|全部|唯一識別該項目。<br /><br /> 元件或類型的名稱前面會加上包含它之套件的限定名稱。<br /><br /> 組件或連接埠的名稱前面會加上擁有它之元件的限定名稱。|  
|**工作項目**|0 associated|全部|與此項目相關聯的工作項目數。 若要關聯工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**描述**|(無)|全部|您可以在這裡設定項目的一般注意事項。|  
|**色彩**|(類型的預設)|元件、組件、委派、組件組譯碼|圖案的色彩。 不像其他屬性，這是圖形的色彩，而不是圖形顯示的模型項目色彩。|  
|**間接具現化**|True|元件|元件只以設計成品方式存在。 在執行階段，只有其組件存在。|  
|**為抽象**|False|元件|元件定義只能用來做為一般化，其他元件可以從中特製化。|  
|**可見度**|Public|元件、組件、連接埠|**公用**-全域可見。<br /><br /> **封裝**-在套件內可見。<br /><br /> **私用**-在主控的元件內可見。<br /><br /> **受保護的**-衍生自擁有者元件可以看到。|  
|**Type**|建立時的類型|組件<br /><br /> 通訊埠|組件的類型是元件或類別。<br /><br /> 連接埠的類型是介面。|  
|**多重性**|1|組件<br /><br /> 通訊埠|表示指定類型形成父元件之組件的執行個體數目。<br /><br /> `1` - 只有一個。<br /><br /> `0..1` - 一或無。<br /><br /> `*` - 任意數目的集合。<br /><br /> `n..m` - 從 n 到 m 個執行個體的集合。|  
|**是的行為**|False|通訊埠|如果為 true，對此連接埠的訊息會由活動或作業來處理，這些活動或元件描述為元件的組件，而非其組件。|  
|**是服務**|False|通訊埠|如果為 true，此連接埠是此元件之已發行介面的組件。|  
|**LinkedPackage**|型號|圖表|加入此圖表之項目的預設命名空間。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 使用案例圖： 參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)



