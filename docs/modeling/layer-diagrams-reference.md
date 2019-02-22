---
title: 相依性圖表參考
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baee97f08a4e6015d6c2e1d88f83f5835431578b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957909"
---
# <a name="dependency-diagrams-reference"></a>相依性圖表： 參考

在 Visual Studio 中，您可以使用*相依性圖表*以視覺化方式檢視您的系統高階邏輯結構。 相依性圖表，您的系統中的實體成品組織成邏輯的抽象群組，稱為*層*。 您可以使用圖層來說明成品或系統主要元件所執行的主要工作。 每個圖層也可以包含巢狀圖層以描述更詳細的工作。

若要查看哪些版本的 Visual Studio 支援此功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

> [!NOTE]
> Visual Studio 2017 中的.NET Core 專案不支援相依性圖表。

您可以指定圖層之間的預期或現有相依性。 這些以箭號代表的相依性，表示哪些圖層可以使用或目前使用其他圖層代表的功能。 藉由將您的系統組織成描述不同角色和功能的層級，相依性圖表有助於讓您更輕鬆地了解、 重複使用，及維護您的程式碼。

使用相依性圖表，可協助您執行下列工作：

-   溝通系統的現有或預期邏輯架構。

-   探索您現有程式碼和預期架構之間的衝突。

-   當重構、更新或發展您的系統時，以視覺化方式檢視變更對預期架構的影響。

-   在開發和維護您的程式碼期間，藉由在簽入及建置作業包含驗證，強化預期的架構。

本主題說明您可以使用相依性圖表的項目。 如需詳細資訊，有關如何建立和繪製相依性圖表，請參閱[相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)。 如需分層模式的詳細資訊，請瀏覽[典範與實例的站台](http://go.microsoft.com/fwlink/?LinkId=145794)。

## <a name="reading-dependency-diagrams"></a>讀取相依性圖表

![在 相依性圖表上的項目](../modeling/media/uml_layerrefreading.png)

下表描述您可以使用相依性圖表的項目。

|**Shape**|**目**|**描述**|
|-|-|-|
|1|**圖層**|您系統中之實體成品的邏輯群組。 這些成品可以是命名空間、專案、類別、方法等等。<br /><br /> 若要查看已連結至圖層的成品，開啟圖層的捷徑功能表，然後選擇**檢視連結**來開啟**圖層總管**。<br /><br /> 如需詳細資訊，請參閱 <<c0> [ 圖層總管](#Explorer)。<br /><br /> -   **Forbidden Namespace Dependencies** -指定與此圖層相關聯的成品不可相依於指定的命名空間。<br />-   **禁止的命名空間**-指定與這個圖層相關聯的成品必須屬於指定的命名空間。<br />-   **必要的命名空間**-指定與這個圖層相關聯的成品必須屬於其中一個指定的命名空間。|
|2|**相依性**|表示一個圖層可以使用另一個圖層的功能，但反之則不然。<br /><br /> -   **方向**-指定相依性的方向。|
|3|**雙向相依性**|表示一個圖層可以使用另一個圖層的功能，反之亦然。<br /><br /> -   **方向**-指定相依性的方向。|
|4|**註解**|用來將一般附註加入圖表或圖表上的項目。|
|5|**註解連結**|用來將註解連結到圖表上的項目。|

## <a name="Explorer"></a> 圖層總管

您可以將每個圖層連結到方案中的成品，例如專案、類別、命名空間、專案檔和您軟體的其他部分。 圖層上的數字顯示連結至該圖層的成品數目。 不過，當閱讀圖層上的成品數時，請記住下列：

-   如果圖層連結的成品有包含其他成品，但圖層未直接連結這些其他成品，則數字將只包含連結的成品。 然而，在圖層驗證期間會加入其他成品以進行分析。

     例如，如果圖層連結到單一命名空間，即使命名空間包含類別，連結的成品數目仍為 1。 如果圖層也有命名空間中每個類別的連結，則數字將包含這些已連結的類別。

-   如果圖層包含已連結到成品的其他圖層，即使此容器圖層上的數字未包含那些成品，容器圖層也會連結到那些成品。

如需連結圖層與成品的詳細資訊，請參閱：

-   [相依性圖表中：指導方針](../modeling/layer-diagrams-guidelines.md)

-   [從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>檢查連結的成品

在相依性圖表中，開啟一或多個圖層的捷徑功能表，然後再選擇**檢視連結**。

**圖層總管**隨即開啟並顯示連結至所選的圖層的成品。 **圖層總管**有一個資料行顯示每個成品連結的屬性。

> [!NOTE]
> 如果您無法看到所有這些屬性，依序展開**圖層總管**視窗。

|**在圖層總管 中的資料行**|**描述**|
|-|-|
|**類別目錄**|成品的類型，例如類別、命名空間、原始程式檔等等|
|**圖層**|連結到成品的圖層|
|**支援驗證**|如果 **，則為 True**，則圖層驗證程序可確認專案符合相依性，或從這個項目。<br /><br /> 如果**False**，則連結不會參與圖層驗證程序。<br /><br /> 如需詳細資訊，請參閱[相依性圖表：指導方針](../modeling/layer-diagrams-guidelines.md)。|
|**識別碼**|連結成品的參考|

## <a name="see-also"></a>另請參閱

- [建立應用程式模型](../modeling/create-models-for-your-app.md)
