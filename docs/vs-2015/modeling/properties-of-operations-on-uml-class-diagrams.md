---
title: 屬性的作業，在 UML 類別圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9d53c44a70818739e02c34071fd81b8bdfdec87f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944216"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML 類別圖上作業的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 UML 類別圖中，新增*作業*加入類別和介面。 作業是一個方法或函式，可由類別或介面的執行個體所執行。  

 若要加入作業，以滑鼠右鍵按一下類別或介面，指向**新增**，然後按一下**作業**。  

 如果在圖表上看不到類別的作業，請按一下類別或介面頂端的展開＞形箭號。 如果您所見**作業**標頭中，按一下 **[+]** 以展開 [作業] 區段。  

## <a name="signature-of-an-operation"></a>作業的簽章  
 作業的簽章是文字行，可在 UML 類別圖的類別或介面中代表它。 其形式如下：  

 \+ OperationName (parameter1:Type1 [*]...):ReturnType [\*]  

 \+ 表示公用可視性。 其他允許的值是 - (private)、# (protected)、~ (package)。  

 `OperationName` 如果要加上底線**Is Static**屬性為 true，則為斜體如果**Is Abstract**屬性為 true。  

 如果未定義傳回類型，則會省略 `: ReturnType`。  

 `[*]` 表示參數或傳回類型的多重性。 如果多重性為 1，則會予以省略。  

 如需這些屬性的完整描述，請參閱下一節。  

## <a name="properties"></a>屬性  
 這些是 UML 類別圖上類別或介面中作業的屬性。  

 若要查看作業的屬性，以滑鼠右鍵按一下類別或介面中的作業，即可在圖表中，然後**屬性**。 屬性會出現在**屬性**視窗。  


|      屬性       |   預設值    |                                                                                                                                                                                 描述                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **名稱**       | (新名稱) |                                                                                                                                                                在包含類型內應該是唯一的。                                                                                                                                                                 |
|   **參數**    |    (無)    |      具有表單的清單<em>名稱</em>**:**<em>型別</em>**，** <em>名稱</em>**:** <em>型別</em>**，...** 按一下  **[...]** 以編輯的清單。<br /><br /> 類型可以是基本類型或是模型中所定義的類型。 如果您在這個屬性中輸入新類型的名稱，系統會將類型加入 UML 模型總管的 [未指定的類型]  區段。      |
|   **傳回型別**   |    (無)    |                                                                               **（無）**，或基本類型或模型中所定義的類型。 如果您在這個屬性中輸入新類型的名稱，系統會將類型加入 UML 模型總管的 [未指定的類型]  區段。                                                                                |
| **後置條件**  |    (無)    |                                                                                                                         選擇性條件，指定作業執行前後之系統狀態間的關聯性。                                                                                                                         |
|  **前置條件**  |    (無)    |                                                                                                                            選擇性條件，指定作業開始執行前之系統狀態的假設。                                                                                                                            |
| **主體條件** |    (無)    |                                                                                                                                                       作業所傳回值的選擇性條件約束。                                                                                                                                                       |
|   **可見度**    |    Public    |                  允許值以及簽章中出現的字元如下：<br /><br /> **+ Public** - 全域可見<br /><br /> **- Private** - 在擁有類型外部看不到<br /><br /> **# Protected** - 衍生自擁有者的類型可以看到<br /><br /> **~ Package** - 相同套件內的其他類型可以看到。                   |
|    **簽章**    |  +*Name*()   |                                                                                      彙總這個作業的可視性、名稱、參數和傳回類型。 編輯圖表上的簽章，或者編輯個別屬性，即可變更這些屬性。                                                                                      |
|   **工作項目**    | 0 associated |                                                                                                  相關聯工作項目計數。 唯讀。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。                                                                                                  |
|   **並行**   |  循序  | **循序**-作業或會設計成沒有並行控制。 同時呼叫這項作業可能會導致失敗。<br /><br /> **受防護**-它的其他執行個體完成之前，將會自動封鎖作業。<br /><br /> **並行**-作業設計成可同時執行多個呼叫。 |
|    **為靜態**    |    False     |                                                                                                  若為 true，則會在這類型的所有執行個體之間共用這項作業。<br /><br /> 若為 true，則作業名稱出現在圖表上時會加上底線。                                                                                                   |
|   **為抽象**   |    False     |                                                                                                                                        若為 true，則沒有程式碼與這項作業相關聯。 因此，主控類別是抽象的。                                                                                                                                         |
|     **是分葉**     |    False     |                                                                                                                                              設計工具預設無法覆寫衍生類別中的這項作業。                                                                                                                                              |
|    **是查詢**     |    False     |                                                                                                 若為 true，這項作業不會對系統狀態進行重大變更。 因此，例如，它可以用於測試來檢查系統狀態。                                                                                                  |
|  **多重性**   |      1       |                                 **1** -指定型別的單一值。<br /><br /> **0..1** -可以是`null`。<br /><br /> \* -指定型別的值的集合。<br /><br /> **1..\\**  \* -集合，其中包含至少一個值。<br /><br /> *n* `..` *m* -集合，其中包含之間`n`和`m`值。                                  |
|   **排序**    |    False     |                                                                                                                                             如果為 true，則集合會形成循序清單。 針對**多重性**1 個以上。                                                                                                                                              |
|    **是唯一的**    |    False     |                                                                                                                                         如果為 true，則集合中沒有重複值。 針對**多重性**1 個以上。                                                                                                                                         |

## <a name="see-also"></a>另請參閱  
 [UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 類別圖上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [在 UML 類別圖上的屬性的屬性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [在 UML 類別圖上的關聯性的屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML 類別圖表：方針](../modeling/uml-class-diagrams-guidelines.md)
