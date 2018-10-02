---
title: 讀取模型和其他 Visual Studio 版本中的圖表 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a4642086639fad8a5b39e4a03d4509b349807a9b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "47588785"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>在其他 Visual Studio 版本中讀取模型和圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[讀取模型和其他 Visual Studio 版本中的圖表](https://docs.microsoft.com/visualstudio/modeling/read-models-and-diagrams-in-other-visual-studio-editions)。  
  
在不支援模型建立的 Visual Studio 版本中開啟模型時，會以唯讀模式開啟模型。 在此模式中，您可以變更圖表的版面配置，但是無法變更模型。  
  
 若要查看哪些版本的 Visual Studio 支援模型建立，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>取得模型和圖表的存取權  
 若要讀取 UML 圖表或分層圖，您必須先使用 Visual Studio 開啟模型專案中，，然後開啟 其內的圖表。  
  
 基於這個理由，如果您想要讀取 UML 圖表或分層圖，則也必須存取在其中建立它的模型專案。 從 [!INCLUDE[esprscc](../includes/esprscc-md.md)] 存取專案，或取得專案檔複本，即可完成這項作業。  
  
> [!NOTE]
>  這不適用於透過程式碼產生的 Code Map 和 .NET 類別圖。 這些圖表可以與模型專案分開檢視。  
  
 若要讀取 UML 圖表或分層圖，您需要的最小檔案集如下：  
  
-   兩個圖表檔，例如，想要讀取之圖表**MyDiagram.classdiagram 和 MyDiagram.classdiagram.layout**。  
  
    > [!NOTE]
    >  對於分層圖，您應該也有檔案，稱為_MyDiagram_**。 layerdiagram.suppressions**。  
  
-   模型專案檔 (**MyModel.modelproj**)  
  
-   根模型檔 (**ModelDefinition\MyModel.uml**)  
  
-   在圖表中所參考之任何套件的套件檔案 (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>您可以在唯讀模式中進行的變更  
 如果您在不支援模型建立的 Visual Studio 版本中開啟模型和其圖表，則無法變更模型。 也就是說，您無法變更圖表或模型總管中所顯示的項目和關聯性。 不過，您可以對圖表的版面配置進行一些變更：  
  
-   重新排列圖表上的圖形和連接器。  
  
-   展開和摺疊圖形。  
  
 您可以儲存這些變更。 如果您想要讓您變更其他使用者看到，您必須至少傳送更新過 **.layout**檔案。  
  
##  <a name="RelatedTopics"></a> 相關的主題  
  
|標題|描述|  
|-----------|-----------------|  
|[分層圖：參考](../modeling/layer-diagrams-reference.md)|分層圖會顯示現有或提議之架構的結構。 撰寫程式碼時，可以針對分層圖自動進行驗證。|  
|[UML 活動圖表：參考](../modeling/uml-activity-diagrams-reference.md)|活動圖顯示商務流程或軟體中的工作流程。|  
|[UML 類別圖表：參考](../modeling/uml-class-diagrams-reference.md)|類別圖顯示許多內容中所使用的類型和關聯性，例如程式碼、資料庫結構描述、通訊協定，或用來描述商務網域的詞彙。|  
|[UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)|元件圖顯示軟體設計中的不同部分和其介面。|  
|[UML 順序圖表：參考](../modeling/uml-sequence-diagrams-reference.md)|循序圖顯示軟體設計中項目之間的互動。|  
|[UML 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)|使用案例圖顯示系統使用者，以及他們可執行以達成特定目標的活動。|  
  
## <a name="see-also"></a>另請參閱  
 [建立應用程式模型](../modeling/create-models-for-your-app.md)



