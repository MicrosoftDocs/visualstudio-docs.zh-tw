---
title: 類別圖表中的 uml 的關聯性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 96dc1d942a06e4030992889970fd3946d2e4d9d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485085"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>UML 類別圖上的關聯性屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[屬性的關聯性，在 UML 類別圖](https://docs.microsoft.com/visualstudio/modeling/properties-of-associations-on-uml-class-diagrams)。  
  
在 UML 類別圖中，您可以繪製*關聯*之間任何一對類型。 類型為類別、介面或列舉。  
  
 關聯表示您正在開發的系統會儲存關聯類型的執行個體之間的某種連結。 一般而言，它並未針對連結實作有任何暗示。 比方說，它們可能是指標、資料表中的資料列、XML 中的交互參考名稱等等。  
  
 關聯是顯示屬性或一對屬性的圖表方法。 例如，如果您已經定義類別 Restaurant 具有類型 Menu 的屬性，您可以藉由繪製 Restaurant 和 Menu 之間的關聯來陳述相同的定義。  
  
 若要繪製關聯時，按一下**關聯**在工具箱中，按一下第一種類型，則第二個。 您可以按一下相同的類型兩次，以顯示執行個體可以連結相同類型的其他執行個體。  
  
## <a name="properties"></a>屬性  
 這些是 UML 類別圖上的關聯屬性。  
  
 若要查看關聯的屬性，以滑鼠右鍵按一下關聯，然後按一下**屬性**。 屬性隨即出現於 [屬性] 視窗中。  
  
 部分屬性也會顯示在圖表中，如下圖所示。  
  
 ![關聯的屬性](../modeling/media/uml-classprop.png "UML_ClassProp")  
  
|**Property**|描述|  
|------------------|-----------------|  
|**名稱 (1)**|識別關聯。 這也會顯示在圖表上，接近關聯的中間點位置。|  
|**限定的名稱**|唯一地識別關聯。 前置字元為包含關聯第一個角色之套件的限定名稱。|  
|**工作項目**|連結到此關聯的工作項目數目。 若要連結工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**色彩**|連接器的色彩。 不同於其他屬性，這是此關聯檢視的屬性，而不是模型中基礎關聯性的屬性。|  
|**第一個角色**<br /><br /> **第二個角色**|關聯的每一端稱為角色。 每個角色描述關聯相反端之類別上之對等屬性的屬性。<br /><br /> 在範例圖表中，Menu 和 Menu Item 之間的關聯具有稱為 Menu 和 Contents 的角色。<br /><br /> Contents 是 Menu 類別上的屬性名稱。|  
  
### <a name="properties-of-each-role"></a>每個角色的屬性  
 若要查看每個角色的內容，依序展開**第一個角色**或是**第二個角色**屬性。  
  
|**Property**|**Default**|描述|  
|------------------|-----------------|-----------------|  
|**角色名稱 (2)**|在這個角色的類型名稱|角色的名稱。 顯示在圖表上接近關聯一端的位置。|  
|**彙總**|無|**無**(4)-代表類別的執行個體之間的一般關聯性。<br /><br /> **複合**(5) 位在這個角色包含位於相反角色的物件。 您可以使用**複合**工具來建立與複合彙總的關聯。<br /><br /> **共用**(6)-在這個角色包含在另一個角色物件的參考。 您可以使用**彙總**工具來建立與共用彙總的關聯。<br /><br /> 確切的解譯方式由本機慣例決定。|  
|**衍生**|False|如果為 true，在連結這一端的物件會從其他屬性和關聯計算。 例如，從 MyEmployer.WorkPlace 計算 MyWorkPlace。 詳細資料應該輸入到描述或附加的註解中。|  
|**是衍生等位**|False|如果為 true，則角色是衍生類型之一組角色的聯集。|  
|**是可瀏覽**|True|可以從此方向閱讀關聯。 假設是相反角色的執行個體，您正在描述的軟體可以有效率地判斷此角色的關聯執行個體。<br /><br /> 如果一個角色是 Navigable，另一個不是，則會在巡覽方向的關聯上出現箭頭 (7)。<br /><br /> 根據預設，關聯工具會建立可以從一個方向巡覽的關聯。 若要將它轉換成雙向關聯，您可以選取的關聯，按一下 [動作] 標籤，會出現，然後按一下**成為雙向**。|  
|**是唯讀的**|False|如果為 true，則建立之後便無法變更關聯的執行個體。 連結永遠是針對相同的物件。|  
|**多重性 (3)**|1|**1** -一律關聯這一端連結至一個物件。 在此圖中，每個 Menu Item 會有一個 Menu。<br /><br /> **0..1** -其中一個關聯這一端連結至一個物件，或沒有連結。<br /><br /> **\*** -關聯另一端的每個物件會連結至這一端物件的集合，而且可能是空的集合。<br /><br /> **1..\***  -關聯另一端的每個物件連結到這一端的至少一個物件。 在圖中，每個 Menu 有至少一個 Menu Item。<br /><br /> *n* **..** *m* -另一端的每個物件有一個集合之間*n*並*m*這一端物件的連結。|  
|**排序**|False|如果為 true，傳回的集合會形成循序清單。 超過 1 的 [多重性]。|  
|**是唯一的**|False|如果為 true，傳回的集合中沒有重複值。 超過 1 的 [多重性]。|  
|**可見度**|Public|Public - 全域可見<br /><br /> Private - 在擁有類型外部看不到<br /><br /> Protected - 衍生自擁有者的類型可以看到<br /><br /> Package - 相同套件內的其他類型可以看到。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 類別圖上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [在 UML 類別圖上的屬性的屬性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML 類別圖上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)



