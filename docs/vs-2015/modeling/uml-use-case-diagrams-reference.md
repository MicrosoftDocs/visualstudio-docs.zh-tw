---
title: UML 使用案例圖： 參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9fbdf85b3177b88e1a7e97f3cbcd4f901961958d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256304"
---
# <a name="uml-use-case-diagrams-reference"></a>UML 使用案例圖表：參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，*使用案例圖*摘要說明哪些人使用您的應用程式或系統，以及他們可以使用它做什麼。 若要建立 UML 使用案例圖表，在**架構**功能表上，按一下**新增 UML 或分層圖**。  
  
 使用案例圖可當做使用者需求描述的焦點。 它會描述需求、使用者和主要元件之間的關聯性。 它不會詳細描述需求；這些可以在個別的圖表或文件中描述，而這些圖表或文件可以連結到各個使用案例。 如需使用案例圖可協助您了解、 討論和溝通使用者需求的資訊，請參閱[模型使用者需求](../modeling/model-user-requirements.md)。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
> [!NOTE]
>  本主題描述使用案例圖中可用的項目。 如需如何繪製使用案例圖的詳細資訊，請參閱[UML 使用案例圖： 方針](../modeling/uml-use-case-diagrams-guidelines.md)。 如需如何建立和繪製模型圖表的詳細資訊，請參閱[編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)。  
  
## <a name="reading-use-case-diagrams"></a>閱讀使用案例圖  
 下節中的各表將描述使用案例圖上可用的項目，以及其主要屬性。 如需的屬性完整清單，請參閱 <<c0> [ 屬性中的項目 UML 使用案例圖](../modeling/properties-of-elements-on-uml-use-case-diagrams.md)。  
  
### <a name="actors-use-cases-and-subsystems"></a>執行者、使用案例及子系統  
 ![使用案例圖中的項目](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
|**圖形**|**目**|**描述和主要屬性**|  
|---------------|-----------------|-----------------------------------------|  
|1|**動作項目**|代表與您的應用程式或系統互動的使用者、組織或外部系統。 執行者是一種類型。<br /><br /> -   **影像路徑**-應該用於取代預設執行者圖示的影像的檔案路徑。 此圖示應為 Visual Studio 專案內的資源檔。|  
|2|**使用案例**|代表一個或多個執行者為達成特定目標所執行的動作。 使用案例是一種類型。<br /><br /> -   **主體**-顯示使用案例的子系統。|  
|3|**關聯**|表示執行者參與使用案例。|  
|4|**子系統或元件**|您使用的系統或應用程式，或其中一部分。 可以是大型網路，也可以是應用程式中的單一類別。<br /><br /> 系統或元件支援的使用案例會出現在自己的矩形內。 它可用來在矩形外顯示某些使用案例，以便釐清系統的範圍。<br /><br /> 基本上，使用案例圖中的子系統擁有與元件圖中元件相同的類型。<br /><br /> -   **已間接具現化**-如果為 false，您執行的系統有一個或多個物件直接對應到這個子系統。 如果為 true，則此子系統是設計中的建構，只有透過具現化其構成部分才會出現在執行系統中。|  
  
### <a name="structuring-use-cases"></a>建構使用案例  
 ![包含使用案例、 擴充和一般化](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")  
  
|圖形|**目**|描述|  
|-----------|-----------------|-----------------|  
|5|**包含**|包含的使用案例會呼叫或叫用被包含的使用案例。 「包含」(Inclusion) 可用來顯示如何將使用案例細分成更小的步驟。 被包含的使用案例位於箭頭末端。<br /><br /> 請注意，此圖表不會顯示步驟的順序。 您可以使用活動圖、循序圖或其他文件來描述這些詳細資料。|  
|6|**擴充**|擴充使用案例會將目標和步驟加入被擴充的使用案例。 擴充功能只能在特定條件下執行。 被擴充的使用案例位於箭頭末端。<br /><br /> 請注意，此圖表不會顯示適用擴充功能之確切的情況：您可以將這些情況記錄在註解或其他文件中。|  
|7|**繼承**|建立特製化和一般化項目的關聯。 一般化項目位於箭頭末端。<br /><br /> 特製化使用案例會繼承其一般化的目標和執行者，而且會加入更特定的目標和步驟來達成目的。<br /><br /> 特製化執行者會繼承其一般化的使用案例、屬性和關聯，而且可能還會加入更多。|  
|8|**相依性**|表示此來源的設計是根據該目標的設計而定。|  
|9|**註解**|用來將一般記事加入此圖表。|  
|10|**成品**|成品提供另一個圖表或文件的連結。 您可以從 [方案總管] 中拖曳檔案來建立成品。 成品可透過「相依性」與該圖表上的任何其他項目連結。 成品的常見用途是將使用案例連結至提供其詳細描述的循序圖、OneNote 頁面、Word 文件或 PowerPoint 簡報。 此文件可以是 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 方案中的項目，或是共用位置 (如 SharePoint 網站) 中的文件。<br /><br /> -   **超連結**。 此圖表或文件的 URL 或檔案路徑。<br /><br /> 按兩下成品，即可開啟成品所連結的檔案或網頁。|  
|11 (未顯示)|**封裝**|使用案例、執行者和子系統可以包含在套件內。 套件圖形不會出現在圖表中，但是您可以設定**LinkedPackage**圖表的屬性。 您後續在此圖表上建立的項目會放在該套件內。 如需詳細資訊，請參閱 <<c0> [ 定義套件和命名空間](../modeling/define-packages-and-namespaces.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [UML 使用案例圖： 方針](../modeling/uml-use-case-diagrams-guidelines.md)   
 [編輯 UML 模型和圖表](../modeling/edit-uml-models-and-diagrams.md)   
 [UML 循序圖： 參考](../modeling/uml-sequence-diagrams-reference.md)   
 [UML 類別圖： 參考](../modeling/uml-class-diagrams-reference.md)   
 [UML 元件圖： 參考](../modeling/uml-component-diagrams-reference.md)   
 [UML 元件圖表：參考](../modeling/uml-component-diagrams-reference.md)



