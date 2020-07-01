---
title: UML 活動圖：參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 960e9469290bca42abd252d497c2ce72e62e41a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531530"
---
# <a name="uml-activity-diagrams-reference"></a>UML 活動圖表：參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*活動圖*會透過一系列的動作，將商務程式或軟體流程顯示為工作流程。 人員、軟體元件或電腦皆可執行這些動作。

 您可以使用活動圖描述多種類型的程序，如下所示：

- 商務程序或使用者與系統之間的工作流程。 如需詳細資訊，請參閱[模型使用者需求](../modeling/model-user-requirements.md)。

- 使用案例的執行步驟。 如需詳細資訊，請參閱[UML 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)。

- 軟體通訊協定，也就是元件之間允許的互動序列。

- 軟體演算法。

  本主題描述活動圖中可以使用的項目。 如需繪製活動圖的詳細資訊，請參閱[UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)。 若要建立 UML 活動圖，請在 [**架構**] 功能表上，按一下 [**新增 UML 或分層圖**]。 如需如何在一般情況下繪製模型圖表的詳細資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。

## <a name="reading-activity-diagrams"></a>讀取活動圖
 下列各節中的表格，會描述活動圖的可用項目及其主要屬性。 如需專案屬性的完整清單，請參閱[UML 活動圖上元素的屬性](../modeling/properties-of-elements-on-uml-activity-diagrams.md)。

 動作和出現在活動圖中的其他項目，會形成一個活動。 您可以在 [UML 模型總管] 中查看活動。 它在您於圖中加入第一個項目時即建立。

 讀圖時，請想像語彙基元或控制項的執行緒，沿著連接器一個動作接一個動作地傳送下去。

### <a name="simple-control-flows"></a>簡單的控制流程
 您可以用分支與迴圈顯示一連串動作。 如需如何使用此處所述之元素的詳細資訊，請參閱[UML 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)主題中的描述控制流程一節。

 ![簡單的控制流程](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

|**多邊形**|**元素**|**描述和主要屬性**|
|-|-|-|
|1|**動作**|活動的一個步驟，使用者或軟體在此會執行某些工作。<br /><br /> 此動作會在語彙基元抵達其所有流入流程時啟動。 結束時，語彙基元會傳送到所有的流出流程。<br /><br /> -   **Body** -詳細指定動作。<br />-   **Language** -主體中運算式的語言。<br />-   **本機後置條件**-執行結束時必須滿足的條件約束。 藉由動作所達成的目標。<br />-   **本機前置條件**-開始執行之前必須滿足的條件約束。|
|2|**控制流程**|顯示動作間控制流程的連接器。 解譯圖表時，請想像語彙基元從一個動作流向下一個動作。<br /><br /> 若要建立控制流程，請使用**Connector**工具。|
|3|**初始節點**|指出活動裡的第一個或前幾個動作。 當活動啟動時，語彙基元就會從初始節點流動。|
|4|**活動的最後節點**|活動結束。 當語彙基元抵達時，活動便會終止。|
|5|**決策節點**|流程圖中的條件分支。 有一個輸入和兩個或多個輸出。 傳入的語彙基元只會顯露在其中一個輸出上。|
|6|**防範**|指定語彙基元是否可以沿著連接器流動的條件。 最常用於決策節點的流出流程。<br /><br /> 若要設定防護，請以滑鼠右鍵按一下流程，再按一下 [**屬性**]，然後設定 [ **guard** ] 屬性。|
|7|**合併節點**|需要合併使用決策節點分割的流程。 有兩個或多個輸入和一個輸出。 在任何輸入上的語彙基元會顯露在輸出上。|
|8|**註解**|提供所連結項目的其他資訊。|
|9|**呼叫行為動作**|更詳細定義在另一個活動圖上的動作。<br /><br /> -   **IsSynchronous** -如果為 true，則動作會等到活動終止為止。<br />-   **行為**-叫用的活動。|
|(未顯示)|**呼叫作業動作**|呼叫類別執行個體上作業的動作。|
||**活動**|活動圖表描述的工作流程。 若要查看活動的屬性，您必須在 [ **UML 模型瀏覽器**] 中選取它。<br /><br /> -   **為唯讀**-如果為 true，則活動不應該變更任何物件的狀態。<br />-   **是單一執行**-如果為 true，則此圖表最多一次執行。|
||**UML 活動圖表**|顯示活動的圖表。 若要查看其屬性，請按一下圖表的空白部分。 **注意：** 活動圖的名稱、包含圖表的檔案，以及圖表所顯示的活動都可以不同。|

### <a name="concurrent-flows"></a>並行流程
 您可以描述同一時間執行的動作順序。 如需詳細資訊，請參閱＜繪製並行流程＞。

 ![顯示並行流程的活動圖表](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

|**多邊形**|**元素**|**描述**|
|-|-|-|
|11|**分岔節點**|將單一流程分割成並行流程。 每個傳入的語彙基元都會在每個傳出的連接器上產生語彙基元。|
|12|**聯結節點**|將並行流程結合成單一流程。 當每個流入流程都有語彙基元在等候時，輸出上就會產生語彙基元。|
|13|**傳送訊號動作**|這個動作會將訊息或信號傳送到另一個活動，或傳送到相同活動中的並行執行緒。 訊息的類型和內容是由動作標題暗示，或在其他註解中指定。<br /><br /> 動作可以在信號中傳送資料，這些資料可以傳遞給物件流程或輸入連接 (16) 中的動作。|
|14|**接受事件動作**|先等待訊息或信號再繼續的動作。 動作可以接收的訊息類型，是由標題暗示或在其他註解中指定。<br /><br /> 如果動作沒有傳入的控制流程，只要接收到訊息就會產生語彙基元。<br /><br /> 動作可以接收信號中的資料，這些資料可在物件流程或輸出連接 (17) 上傳遞。<br /><br /> -   **IsUnmarshall** -如果為 true，則可以有數個具類型的輸出連接，並將資料 unmarshalled 到這些釘選。 如果為 false，所有資料會顯示在一個連接上。|

### <a name="data-flows"></a><a name="DataFlow"></a>資料流程
 您可以描述動作到動作的資料流程。 如需本節所用項目的詳細資訊，請參閱＜活動圖繪製方針＞主題的＜繪製資料流程＞一節。

 ![顯示資料流程的活動圖表](../modeling/media/uml-actovdata.png "UML_ActOvData")

|**多邊形**|**元素**|**描述**|
|-|-|-|
|15|**物件節點**|表示順著流程傳遞的資料。<br /><br /> -   **排序**-多個標記的儲存方式。<br />-   **選取**-叫用可在另一個圖表中定義的處理常式，以篩選資料。<br />-   **上限**-0 表示資料必須直接沿著流程傳遞;\*表示資料可以儲存在流程中。<br />-   **類型**-儲存和傳輸的物件類型。|
|16|**輸入連接**|表示動作執行時可以接收的資料。<br /><br /> -   **類型**-傳輸的物件類型。|
|17|**輸出連接**|表示動作執行時所產生的資料。<br /><br /> -   **類型**-傳輸的物件類型。|
|18|**活動參數節點**|物件節點，資料可以透過它被活動接收或產生。<br /><br /> 使用時機為從另一個活動呼叫圖表所表示的活動，或圖表說明作業或函式時。<br /><br /> -   **類型**-傳輸的物件類型。|
|(未顯示)|**物件流程**|顯示動作與物件節點間資料流程的連接器。<br /><br /> 若要建立物件流程，請使用 [**連接器**] 工具，將輸入或輸出連接或物件節點連結至另一個元素。<br /><br /> -   **選取**-叫用可在另一個圖表中定義的處理常式，以篩選資料。<br />-   **轉換**-叫用可在另一個圖表中定義的處理常式，以轉換資料。<br />-   **IsMulticast** -表示可能有數個收件者物件或元件。<br />-   **IsMultiReceive** -指出可以從數個物件或元件接收輸入。|

## <a name="see-also"></a>另請參閱
 [編輯 uml 模型和圖表](../modeling/edit-uml-models-and-diagrams.md) [uml 活動圖：方針](../modeling/uml-activity-diagrams-guidelines.md)
