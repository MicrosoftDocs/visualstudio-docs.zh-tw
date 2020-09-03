---
title: UML 類別圖表上類型的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671324"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML 類別圖上的類型屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 類別圖中， *類型* 為類別、介面或列舉。

> [!NOTE]
> 本主題是有關 UML 類別圖中類型的屬性。 如需詳細資訊，請參閱下列主題：

- [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)

- [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)

- [UML 類別圖表中屬性 (Attribute) 的屬性 (Property)](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML 類別圖表上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML 類別圖表上的關聯屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>屬性
 這些是類別、介面或列舉的屬性。

 若要查看類型的屬性，請以滑鼠右鍵按一下圖表或 [ **UML 模型瀏覽器**] 中的類型，然後按一下 [ **屬性**]。 屬性會出現在 [ **屬性** ] 視窗中。

|**屬性**|**預設值**|顯示位置|描述|
|------------------|-----------------|----------------|-----------------|
|**名稱**|預設名稱|所有項目|識別項目。|
|**完整名稱**|包含套件 :: 類型名稱|所有項目|唯一識別該項目。 前面加上含有該項目之套件的合格名稱。|
|**色彩**|(這類類型的預設值)|所有項目|圖形的色彩。 與其他屬性不同，這不是基礎圖形項目的屬性。 相同類型的不同檢視可以有不同的色彩。|
|**是否為抽象**|否|類別|如果為 true，則無法具現化類別，而是做為基底類別。|
|**Is Leaf**|否|類別、介面|如果為 true，類型並不適合具有衍生類型。|
|**為使用中**|否|類別|如果是 true，則這個類型的每個執行個體都會與控制項的執行緒相關聯。|
|**可見性**|公用|類別、介面、列舉|-Public-全域可見。<br />-Private-在擁有它的封裝內可以看到這個型別。<br />-Package-在套件內可見。|
|**工作專案**|0 associated|所有項目|與此項目相關聯的工作項目數。 若要建立工作專案的關聯，請參閱 [連結模型專案和工作專案](../modeling/link-model-elements-and-work-items.md)。|
|**描述**|(空白)|所有項目|您可以在這裡設定項目的一般注意事項。|
|**範本系結**|(無)|類別、介面、列舉|如果不是空白，則此類型是透過將參數值繫結至這個樣板類別所定義。 展開屬性，以查看範本參數的繫結。|
|**範本參數**|(無)|類別、介面、列舉|如果不是空白，則這是具有這裡所列之參數的樣板類別。 若要加入參數或查看個別參數的屬性，請按一下 **[...]**。|

## <a name="see-also"></a>另請參閱
 Uml 類別圖表上[關聯](../modeling/properties-of-associations-on-uml-class-diagrams.md)uml 類別[圖屬性上](../modeling/properties-of-operations-on-uml-class-diagrams.md)uml 類別圖表上的[屬性屬性 uml](../modeling/properties-of-attributes-on-uml-class-diagrams.md)類別圖表[：方針](../modeling/uml-class-diagrams-guidelines.md)
