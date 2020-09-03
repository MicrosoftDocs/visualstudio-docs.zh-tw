---
title: UML 元件圖上的元素屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671454"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>UML 元件圖中的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 元件圖中，圖表上的每個項目都會有屬性。 若要查看專案的屬性，請以滑鼠右鍵按一下圖表或 [ **UML 模型瀏覽器** ] 中的元素，然後按一下 [ **屬性**]。 屬性會出現在 [ **屬性** ] 視窗中。

> [!NOTE]
> 本主題有關 UML 元件圖中的項目屬性。 如需如何讀取 UML 元件圖的詳細資訊，請參閱 [Uml 元件圖：參考](../modeling/uml-component-diagrams-reference.md)。 如需如何繪製 UML 元件圖的詳細資訊，請參閱 [Uml 元件圖：方針](../modeling/uml-component-diagrams-guidelines.md)。

## <a name="properties-of-elements"></a>項目屬性

|屬性|預設|項目|描述|
|--------------|-------------|-------------|-----------------|
|**名稱**|預設名稱|全部|識別項目。|
|**完整名稱**|命名空間 :: 名稱|全部|唯一識別該項目。<br /><br /> 元件或類型的名稱前面會加上包含它之套件的限定名稱。<br /><br /> 組件或連接埠的名稱前面會加上擁有它之元件的限定名稱。|
|**工作專案**|0 associated|全部|與此項目相關聯的工作項目數。 若要建立工作專案的關聯，請參閱 [連結模型專案和工作專案](../modeling/link-model-elements-and-work-items.md)。|
|**描述**|(無)|全部|您可以在這裡設定項目的一般注意事項。|
|**色彩**|(類型的預設)|元件、組件、委派、組件組譯碼|圖案的色彩。 不像其他屬性，這是圖形的色彩，而不是圖形顯示的模型項目色彩。|
|**間接具現化**|是|元件|元件只以設計成品方式存在。 在執行階段，只有其組件存在。|
|**是否為抽象**|否|元件|元件定義只能用來做為一般化，其他元件可以從中特製化。|
|**可見性**|公用|元件、組件、連接埠|**Public** -全域可見。<br /><br /> **封裝-在** 套件內可見。<br /><br /> **私** 用-在擁有元件內可見。<br /><br /> **Protected** -衍生自擁有者的元件可以看見。|
|**類型**|建立時的類型|部分<br /><br /> Port|組件的類型是元件或類別。<br /><br /> 連接埠的類型是介面。|
|**多重性**|1|部分<br /><br /> Port|表示指定類型形成父元件之組件的執行個體數目。<br /><br /> `1` -正好一個。<br /><br /> `0..1` -一或無。<br /><br /> `*` -任何數位的集合。<br /><br /> `n..m` -從 n 到 m 實例的集合。|
|**Is Behavior**|否|Port|如果為 true，對此連接埠的訊息會由活動或作業來處理，這些活動或元件描述為元件的組件，而非其組件。|
|**Is Service**|否|Port|如果為 true，此連接埠是此元件之已發行介面的組件。|
|**LinkedPackage**|型號|圖表|加入此圖表之項目的預設命名空間。|

## <a name="see-also"></a>另請參閱
 [Uml 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md) [Uml 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)
