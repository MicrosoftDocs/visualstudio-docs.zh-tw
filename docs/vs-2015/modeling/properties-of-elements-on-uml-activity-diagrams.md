---
title: UML 活動圖表上元素的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6698f728645d5fb9a38d2a003293c7fadda005d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671446"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>UML 活動圖表中的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 活動圖表上，每個項目都具有屬性。 若要查看元素的屬性，請以滑鼠右鍵按一下圖表上的專案或 [ **UML 模型瀏覽器**]，然後按一下 [**屬性**]。 屬性會出現在 [**屬性**] 視窗中。

> [!NOTE]
> 本主題有關 UML 活動圖表上項目的屬性。 如需如何讀取 UML 活動圖的詳細資訊，請參閱[Uml 活動圖：參考](../modeling/uml-activity-diagrams-reference.md)。 如需如何繪製 UML 活動圖的詳細資訊，請參閱[Uml 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)。

## <a name="properties-of-elements"></a>項目屬性

|         屬性         |        Default         |                               項目                               |                                                                                                                                                                描述                                                                                                                                                                 |
|--------------------------|------------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         **名稱**         |     預設名稱     |                                 All                                 |                                                                                                                                                          識別項目。                                                                                                                                                           |
|    **限定名稱**    |    套件 :: 名稱     |                                 All                                 |                                                                                                                     唯一識別該項目。 前面加上含有該項目之套件的合格名稱。                                                                                                                     |
|      **工作專案**      |      0 associated      |                                 All                                 |                                                                                與此項目相關聯的工作項目數。 若要建立工作專案的關聯，請參閱[連結模型元素和工作專案](../modeling/link-model-elements-and-work-items.md)。                                                                                |
|     **說明**      |         (無)         |                                 All                                 |                                                                                                                                             您可以在這裡設定項目的一般注意事項。                                                                                                                                             |
|        **顏色**         | (類型的預設) |                                 All                                 |                                                                                                                                                          圖案的色彩。                                                                                                                                                           |
|         **本文**         |         (無)         |                               動作                                |                                                                                                                                                      詳細地指定動作。                                                                                                                                                       |
|       **Language**       |         (無)         |                               動作                                |                                                                                                                                                  內容中運算式的語言。                                                                                                                                                   |
| **本機後置條件** |         (無)         |         動作、傳送、接受、呼叫行為、呼叫作業         |                                                                                                                          執行結束時必須滿足的條件約束。 藉由動作所達成的目標。                                                                                                                          |
| **本機前置條件**  |         (無)         |         動作、傳送、接受、呼叫行為、呼叫作業         |                                                                                                                                        執行開始前必須滿足的條件約束。                                                                                                                                         |
|    **為同步**    |          True          |                    呼叫行為、呼叫作業                    |                                                                                                                                        -如果為 true，則動作會等到活動終止為止。                                                                                                                                        |
|       **Behavior**       |         (無)         |                            呼叫行為                            |                                                                                                                                                         -叫用的活動。                                                                                                                                                          |
|      **運營**       |         (無)         |                           呼叫作業                            |                                                                                                                                                         -叫用的作業。                                                                                                                                                         |
|    **為 Unmarshall**     |         False          |                            接受事件                             |                                                                                                       -如果為 true，可能會有數個具類型的輸出插腳，而資料會解除封送到它們。 如果為 False，所有資料會顯示在一個連接上。                                                                                                        |
|     **上限**      |        **\\**\*        |                   物件節點、活動參數                   |                                                                                                      **0**表示資料必須直接沿著流程傳遞。<br /><br /> **\\** \* 表示資料可以儲存在流程中。                                                                                                      |
|      **選取範圍**       |         (無)         | 物件節點、活動參數、輸入連接、輸出連接、物件流程 |                                                                                                                          叫用會篩選資料的處理序。 這個處理序可以在另一個圖表中定義。                                                                                                                          |
|       **排序**       |         (無)         |       物件節點、活動參數、輸入連接、輸出連接        |                                                                                                                                                    -多個標記的儲存方式。                                                                                                                                                     |
|      **為控制項**      |         False          |                        輸入連接、輸出連接                        |                                                                                                                            -如果為 true，則此釘選上的流程是控制流程。 如果為 False，則是物件流程。                                                                                                                            |
|         **Type**         |         (無)         |       輸入連接、輸出連接、物件節點、活動參數        |                              -傳輸的物件類型。<br />-類型可以是基本類型（例如整數），或模型中其他位置所定義的分類器。 如果您輸入未定義之類型的名稱，它會出現在 [UML 模型 Explorer] 的 [**未指定的類型**] 區段中。                               |
|     **數**     |           1            |                        輸入連接、輸出連接                        | -可以是單一值或範圍 `[n..m]`。<br />-下限 `n`-動作無法啟動（針對輸入的 pin）或停止（針對輸出的 pin），直到有 `n` 物件在等候該 pin 為止。<br />-上限 `m`-在一次執行時，動作無法取用或產生超過 `m` 個物件。 \* 表示沒有任何限制。 |
|    **轉換**    |         (無)         |                             物件流程                             |                                                                                                                      -叫用轉換資料的處理常式。 這個處理序可以在另一個圖表中定義。                                                                                                                       |
|     **是否為多播**     |         False          |                             物件流程                             |                                                                                                                                 -表示可能有數個收件者物件或元件。                                                                                                                                 |
|   **為 MultiReceive**    |         False          |                             物件流程                             |                                                                                                                                 -表示可能有數個收件者物件或元件。                                                                                                                                 |
| **為單次執行**  |         False          |                          活動圖                           |                                                                                                                                   -如果設定，此圖表最多一次執行。                                                                                                                                    |

## <a name="see-also"></a>請參閱
 [Uml 活動圖：參考](../modeling/uml-activity-diagrams-reference.md) [uml 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)
