---
title: UML 類別圖：參考 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850172"
---
# <a name="uml-class-diagrams-reference"></a>UML 類別圖：參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML 類別圖描述您的應用程式在內部以及與使用者溝通所使用的物件和資訊結構。 它所描述的資訊不會參考任何特殊實作。 其類別和關聯性可利用許多方式實作，例如資料庫資料表、XML 節點或軟體物件的組合。

> [!NOTE]
> 本主題說明 UML 類別圖。 還有另一種類別圖，也就是 .NET 類別圖，可用來將程式碼視覺化。 如需詳細資訊，請參閱[設計和查看類別和類型](https://msdn.microsoft.com/library/ab7aty24.aspx)。

 若要建立 UML 類別圖，請在 [**架構**] 功能表上，選擇 [**新增 UML 或分層圖**]。 如需如何繪製 UML 類別圖的詳細資訊，請參閱[Uml 類別圖：方針](../modeling/uml-class-diagrams-guidelines.md)。 如需如何建立和繪製模型圖表的詳細資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。

 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="reading-class-diagrams"></a>讀取類別圖
 本節中的表格描述可在 UML 類別圖上看見的項目。 如需這些項目之屬性的詳細資訊，請參閱下列主題：

- [UML 類別圖表上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [UML 類別圖表中屬性 (Attribute) 的屬性 (Property)](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML 類別圖表上作業的屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML 類別圖表上的關聯屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![顯示關聯性和屬性的三個類別](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **多邊形** |       **目**        |                                                                                                                                                             **描述**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **類別**         |                                                           共用指定結構和行為特性之物件的定義。 如需詳細資訊，請參閱[UML 類別圖上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)。                                                            |
|     1     |        分類器        |                                                                                                             類別、介面或列舉的一般名稱。 元件、使用案例和行動也屬於分類器。                                                                                                             |
|     2     | 摺疊/展開控制項 |                                                                                         如果您看不見分類器的詳細資料，請按一下分類器左上角的展開器。 您可能還需要按一下每一個區段的 [+]。                                                                                         |
|     3     |      **屬性**       |   附加至每一個分類器執行個體之類型的值。<br /><br /> 若要新增屬性，請按一下 [**屬性**] 區段，然後按**enter**。 輸入此屬性的簽章。 如需詳細資訊，請參閱[UML 類別圖上屬性的屬性](../modeling/properties-of-attributes-on-uml-class-diagrams.md)。   |
|     4     |      **作業**       | 分類器的執行個體可執行的方法或函式。 若要新增操作，請按一下 [**作業**] 區段，然後按**enter**。 輸入此作業的簽章。 如需詳細資訊，請參閱[UML 類別圖上的作業屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)。 |
|     5     |     **技術協會**      |                                                                  兩個分類器成員之間的關聯性。 如需詳細資訊，請參閱[UML 類別圖上的關聯屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)。                                                                   |
|    5a     |     **彙總**      |                                                                                                    代表共用擁有權關聯性的關聯。 [擁有者] 角色的 [**匯總**] 屬性會設定為 [**共用**]。                                                                                                     |
|    5b     |     **撰寫**      |                                                                                                      代表整體與組成部分之間關聯性的關聯。 [擁有者] 角色的 [**匯總**] 屬性會設定為 [**複合**]。                                                                                                      |
|     6     |   **關聯名稱**   |                                                                                                                                         關聯的名稱。 此名稱可以保持空白。                                                                                                                                          |
|     7     |      **角色名稱**       |                       角色的名稱，也就是關聯的一端。 可以用來表示關聯的物件。 在上圖中，對於任何訂單 (Order) `O`，`O.ChosenMenu` 都是其關聯的菜單 (Menu)。<br /><br /> 每一個角色都有自己的屬性，並且列於關聯的屬性下方。                       |
|     8     |     **多重性**     |                                         表示這一端有多少物件可以連結到另一端的每一個物件。 在此範例中，每一張訂單都必須剛好連結到一張菜單。<br /><br /> **\\** \* 表示可以進行的連結數目沒有上限。                                         |
|     9     |    **通用化**    |  *特定*分類器會從*一般*分類器繼承其定義的一部分。 一般分類器位於連接器的箭號端。 特定分類器會繼承屬性、關聯和作業。<br /><br /> 使用 [**繼承**] 工具可建立兩個分類器之間的一般化。   |

 ![包含介面和列舉的封裝](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|圖形|項目|描述|
|-----------|-------------|-----------------|
|10|**Interface**|物件之一部分外部可見行為的定義。 如需詳細資訊，請參閱[UML 類別圖上的類型屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)。|
|11|**列舉**|由一組常值組成的分類器。|
|12|**套件**|一組分類器、關聯、動作、生命線、元件和套件。 邏輯類別圖會顯示此套件內包含成員分類器和套件。<br /><br /> 名稱會限定在封裝內，讓**傳遞 package1**內的**class1**有別于該封裝外部的**class1** 。 封裝的名稱會顯示為其內容之 [**限定名稱**] 屬性的一部分。<br /><br /> 您可以設定任何 UML 圖表的 [**連結的封裝**] 屬性來參考封裝。 您在圖表上建立的所有項目都將變成套件的一部分。 它們會出現在 [ **UML 模型瀏覽器**] 中的封裝之下。|
|13|**Import**|套件之間的關聯性，表示某一個套件包含另一個套件的所有定義。|
|14|**相依性**|如果箭頭端的分類器已變更，則相依分類器的定義或實作也可能會變更。|

 ![以連接器和棒糖顯示的實現](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|圖形|**目**|描述|
|-----------|-----------------|-----------------|
|15|**價值**|此類別會實作該介面所定義的作業和屬性。<br /><br /> 使用 [**繼承**] 工具可建立類別和介面之間的實現。|
|16|**價值**|相同關聯性的替代表示方式。 棒棒糖符號上的標籤可識別此介面。<br /><br /> 若要建立此表示方式，請選取現有的實現關聯性。 行動標籤會出現在此關聯旁邊。 按一下 [動作] 標記，然後按一下 [**顯示為棒糖**]。|

## <a name="see-also"></a>請參閱
 [編輯 uml 模型和圖表](../modeling/edit-uml-models-and-diagrams.md) [uml 類別圖：](../modeling/uml-class-diagrams-guidelines.md) uml 類別圖上的類型的指導方針[屬性](../modeling/properties-of-types-on-uml-class-diagrams.md)uml 類別圖上的屬性[的屬性 uml](../modeling/properties-of-attributes-on-uml-class-diagrams.md)類別圖上的[關聯](../modeling/properties-of-associations-on-uml-class-diagrams.md)[性屬性](../modeling/properties-of-operations-on-uml-class-diagrams.md)
