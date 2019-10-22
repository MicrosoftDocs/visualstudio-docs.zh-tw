---
title: UML 類別圖上作業的屬性 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671343"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML 類別圖上作業的屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 類別圖上，您可以將*作業*加入至類別和介面。 作業是一個方法或函式，可由類別或介面的執行個體所執行。

 若要新增作業，請以滑鼠右鍵按一下類別或介面，指向 [**加入**]，然後**按一下 [** 作業]。

 如果在圖表上看不到類別的作業，請按一下類別或介面頂端的展開＞形箭號。 如果您可以看到作業**標頭**，請按一下 **[[+]] 展開 [作業]** 區段。

## <a name="signature-of-an-operation"></a>作業的簽章
 作業的簽章是文字行，可在 UML 類別圖的類別或介面中代表它。 其形式如下：

 \+ OperationName （parameter1： Type1 [*]，...）： ReturnType [\*]

 \+ 表示公用可見度。 其他允許的值是 - (private)、# (protected)、~ (package)。

 如果**Is Static**屬性為 true，`OperationName` 會加上底線，如果**is Abstract**屬性為 true，則為斜體。

 如果未定義傳回類型，則會省略 `: ReturnType`。

 `[*]` 表示參數或傳回類型的多重性。 如果多重性為 1，則會予以省略。

 如需這些屬性的完整描述，請參閱下一節。

## <a name="properties"></a>內容
 這些是 UML 類別圖上類別或介面中作業的屬性。

 若要查看作業的屬性，請以滑鼠右鍵按一下圖表上類別或介面中的作業，然後按一下 [**屬性**]。 屬性會出現在 [**屬性**] 視窗中。

|      屬性       |   Default    |                                                                                                                                                                                 描述                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **名稱**       | (新名稱) |                                                                                                                                                                在包含類型內應該是唯一的。                                                                                                                                                                 |
|   **參數**    |    (無)    |      具有 [<em>名稱</em> **：** <em>類型</em>] **、** <em>[名稱</em> **：** <em>類型</em>] **、[...** ] 格式的清單。 按一下 **[...]** 以編輯清單。<br /><br /> 類型可以是基本類型或是模型中所定義的類型。 如果您在這個屬性中輸入新類型的名稱，系統會將類型加入 UML 模型總管的 [未指定的類型] 區段。      |
|   **傳回型別**   |    (無)    |                                                                               **（無）** 、基本類型或模型中定義的類型。 如果您在這個屬性中輸入新類型的名稱，系統會將類型加入 UML 模型總管的 [未指定的類型] 區段。                                                                                |
| **條件**  |    (無)    |                                                                                                                         選擇性條件，指定作業執行前後之系統狀態間的關聯性。                                                                                                                         |
|  **前提**  |    (無)    |                                                                                                                            選擇性條件，指定作業開始執行前之系統狀態的假設。                                                                                                                            |
| **主體條件** |    (無)    |                                                                                                                                                       作業所傳回值的選擇性條件約束。                                                                                                                                                       |
|   **可見度**    |    Public    |                  允許值以及簽章中出現的字元如下：<br /><br /> **+ Public** - 全域可見<br /><br /> **- Private** - 在擁有類型外部看不到<br /><br /> **# Protected** - 衍生自擁有者的類型可以看到<br /><br /> **~ Package** - 相同套件內的其他類型可以看到。                   |
|    **簽章**    |  +*名稱*（）   |                                                                                      彙總這個作業的可視性、名稱、參數和傳回類型。 編輯圖表上的簽章，或者編輯個別屬性，即可變更這些屬性。                                                                                      |
|   **工作專案**    | 0 associated |                                                                                                  相關聯工作項目計數。 唯讀。<br /><br /> 如需詳細資訊，請參閱[連結模型元素和工作專案](../modeling/link-model-elements-and-work-items.md)。                                                                                                  |
|   **並行**   |  循序  | **連續**-作業是或將設計成沒有並行控制。 同時呼叫這項作業可能會導致失敗。<br /><br /> **受**防護-作業會自動封鎖，直到其的其他實例完成為止。<br /><br /> **並行**-作業的設計，讓多個呼叫可以同時執行。 |
|    **為靜態**    |    False     |                                                                                                  若為 true，則會在這類型的所有執行個體之間共用這項作業。<br /><br /> 若為 true，則作業名稱出現在圖表上時會加上底線。                                                                                                   |
|   **為抽象**   |    False     |                                                                                                                                        若為 true，則沒有程式碼與這項作業相關聯。 因此，主控類別是抽象的。                                                                                                                                         |
|     **為分葉**     |    False     |                                                                                                                                              設計工具預設無法覆寫衍生類別中的這項作業。                                                                                                                                              |
|    **Is 查詢**     |    False     |                                                                                                 若為 true，這項作業不會對系統狀態進行重大變更。 因此，例如，它可以用於測試來檢查系統狀態。                                                                                                  |
|  **數**   |      1       |                                 **1** -指定類型的單一值。<br /><br /> **0 ..1** -可以 `null`。<br /><br /> \*-指定之類型的值集合。<br /><br /> **1.. \\** \*-至少包含一個值的集合。<br /><br /> *n* `..` *m* -包含 `n` 和 `m` 值之間的集合。                                  |
|   **已排序**    |    False     |                                                                                                                                             如果為 true，則集合會形成循序清單。 大於1的**多重性**。                                                                                                                                              |
|    **是唯一的**    |    False     |                                                                                                                                         如果為 true，則集合中沒有重複值。 大於1的**多重性**。                                                                                                                                         |

## <a name="see-also"></a>請參閱
 [Uml 類別圖：](../modeling/uml-class-diagrams-reference.md) uml 類別[圖上的](../modeling/properties-of-types-on-uml-class-diagrams.md)型別參考 uml 類別圖[上屬性的](../modeling/properties-of-attributes-on-uml-class-diagrams.md)[屬性 uml 類別](../modeling/properties-of-associations-on-uml-class-diagrams.md)圖[：方針](../modeling/uml-class-diagrams-guidelines.md)
