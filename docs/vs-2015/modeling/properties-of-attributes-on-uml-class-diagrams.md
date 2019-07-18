---
title: 屬性的屬性，在 UML 類別圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24575f125c07a016bef4742e010cbdd51f6c75e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154868"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>UML 類別圖表中屬性 (Attribute) 的屬性 (Property)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 類別圖表中，您可以將 *「屬性」* (Attribute) 加入類別和介面。 屬性會定義可附加至類別或介面執行個體的值。  

 若要加入屬性，請以滑鼠右鍵按一下類別或介面，指向 [加入]  ，然後按一下 [屬性]  。  

 如果看不見圖表上類別的屬性，請按一下類別或介面頂端的＞形箭號將它展開。 如果您看得到 [屬性]  標頭，請按一下 [+]  展開屬性區段。  

## <a name="signature-of-an-attribute"></a>屬性的簽章  
 屬性的簽章是在 UML 類別圖表上的類別或介面中代表該屬性的一行。 其形式如下：  

```  
+ AttributeName : TypeName [*]  
```  

 \+ 表示公用可視性。 其他允許的值是 - (private)、# (protected)、~ (package)。  

 如果屬性是靜態的，`AttributeName` 會加上底線。  

 如果屬性沒有類型，則會省略 `: TypeName`。  

 `[*]` 表示多重性。 如果多重性為 1，則會予以省略。  

## <a name="properties"></a>屬性  
 下表描述 UML 類別圖表上類別或介面中屬性 (Attribute) 的屬性 (Property)。  

 若要查看屬性 (Attribute) 的屬性 (Property)，請以滑鼠右鍵按一下圖表上類別或介面中的屬性 (Attribute)，然後按一下 [屬性]  (Property)。 屬性隨即出現於 [屬性] 視窗中。  

 若要檢視屬性 (Attribute) 的屬性 (Property)，請以滑鼠右鍵按一下它，然後按一下 [屬性]  (Property)。  

|   **Property**    | **Default**  |                                                                                                                                                                                                         說明                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **預設值** |   (空白)    |                                                                                                                                                                               具現化分類器時的屬性值。                                                                                                                                                                                |
| **是唯讀的**  |    False     |                                                                                                                                                                                    如果為 true，則無法變更屬性值。                                                                                                                                                                                    |
|   **為靜態**   |    False     |                                                                                                                    如果為 true，這個屬性的單一值會與這種類型的所有執行個體共用。<br /><br /> 如果為 true，則屬性的名稱會在此圖表上出現的地方加上底線。                                                                                                                    |
|     **名稱**      | (新名稱) |                                                                                                                                                                                        在擁有的分類器內應該是唯一的。                                                                                                                                                                                        |
|     **型別**      |    (無)    |                                                基本類型，例如 [整數]  ，或是在模型中定義的類型。 您無法使用 [十進位]  等非基本類型，因為該值必須以中繼資料編碼。 如果您在這個屬性中輸入新類型的名稱，系統會將類型加入 UML 模型總管的 [未指定的類型]  區段。                                                 |
|  **可見度**   |    Public    |                                     允許值以及簽章中出現的字元如下：<br /><br /> **+ Public** - 全域可見<br /><br /> **- Private** - 在擁有類型外部看不到<br /><br /> **# Protected** - 衍生自擁有者的類型可以看到<br /><br /> **~ Package** - 相同套件內的其他類型可以看到。                                      |
|  **工作項目**   | 0 associated |                                                                                                                          相關聯工作項目計數。 唯讀。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。                                                                                                                           |
|    **是分葉**    |    False     |                                                                                                                                                                    如果為 true，則不允許在衍生類型中重新定義此屬性。                                                                                                                                                                     |
|  **衍生**   |    False     |                                                                                                              如果為 true，則這個屬性是從其他屬性計算而得。 例如，[對角線] 是從 [寬度] 和 [高度] 計算而得。 詳細資料應寫入 [描述]  或附加的 [註解] 中。                                                                                                              |
|  **描述**  |   (空白)    |                                                                                                                                                                        用於一般註解，或是用於定義屬性值的條件約束。                                                                                                                                                                        |
| **多重性**  |      1       | **1** - 這個屬性具有所指定類型的單一值。<br /><br /> **0..1** - 這個屬性可以具有 `null`值。<br /><br /> **\\** \* -此屬性的值是值的集合。<br /><br /> **1..\\**  \* -這個屬性的值是包含至少一個值的集合。<br /><br /> *n* **..** *m* - 這個屬性的值是包含 *n* 到 *m* 個值的集合。 |
|  **排序**   |    False     |                                                                                                                                                                    如果為 true，則集合會形成循序清單。 超過 1 的 [多重性]  。                                                                                                                                                                     |
|   **是唯一的**   |    False     |                                                                                                                                                                如果為 true，則集合中沒有重複值。 超過 1 的 [多重性]  。                                                                                                                                                                |

## <a name="see-also"></a>另請參閱  
 [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 類別圖上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML 類別圖上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML 類別圖表：指導方針](../modeling/uml-class-diagrams-guidelines.md)   
 [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)
