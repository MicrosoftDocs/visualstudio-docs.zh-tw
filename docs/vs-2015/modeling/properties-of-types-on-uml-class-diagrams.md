---
title: 類別圖表上 UML 類型的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: de4bcd2779e448c48bd8ac6e66edf25ef4edddc5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193163"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML 類別圖上的類型屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 類別圖中，*型別*是類別、 介面或列舉型別。  
  
> [!NOTE]
>  本主題是有關 UML 類別圖中類型的屬性。 如需詳細資訊，請參閱下列主題：  
  
-   [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [UML 類別圖表中屬性 (Attribute) 的屬性 (Property)](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [UML 類別圖表上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [UML 類別圖表上的關聯屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>屬性  
 這些是類別、介面或列舉的屬性。  
  
 若要查看類型的屬性，以滑鼠右鍵按一下圖表中或在型別**UML 模型總管**，然後按一下**屬性**。 屬性會出現在**屬性**視窗。  
  
|**Property**|**Default**|會出現在|描述|  
|------------------|-----------------|----------------|-----------------|  
|**名稱**|預設名稱|所有項目|識別項目。|  
|**限定的名稱**|包含套件 :: 類型名稱|所有項目|唯一識別項目。 前面加上含有該項目之套件的合格名稱。|  
|**色彩**|(這類類型的預設值)|所有項目|圖形的色彩。 與其他屬性不同，這不是基礎圖形項目的屬性。 相同類型的不同檢視可以有不同的色彩。|  
|**為抽象**|False|類別|如果為 true，則無法具現化類別，而是做為基底類別。|  
|**是分葉**|False|類別、介面|如果為 true，類型並不適合具有衍生類型。|  
|**作用中**|False|類別|如果是 true，則這個類型的每個執行個體都會與控制項的執行緒相關聯。|  
|**可見度**|Public|類別、介面、列舉|-Public-全域可見。<br />-Private-此類型是在擁有該封裝內為可見。<br />-Package-在套件內可見。|  
|**工作項目**|0 associated|所有項目|與此項目相關聯的工作項目數。 若要關聯工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**描述**|(空白)|所有項目|您可以在這裡設定項目的一般注意事項。|  
|**範本繫結**|(無)|類別、介面、列舉|如果不是空白，則此類型是透過將參數值繫結至這個樣板類別所定義。 展開屬性，以查看範本參數的繫結。|  
|**範本參數**|(無)|類別、介面、列舉|如果不是空白，則這是具有這裡所列之參數的樣板類別。 若要加入參數，或檢視個別參數的屬性，請按一下 **[...]**.|  
  
## <a name="see-also"></a>另請參閱  
 [在 UML 類別圖上的屬性的屬性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML 類別圖上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [在 UML 類別圖上的關聯性的屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)



