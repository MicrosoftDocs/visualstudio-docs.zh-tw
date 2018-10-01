---
title: 使用 UML API 進行程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: aff07c444b6dac85144b06c0430ad1d9a2a497c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490115"
---
# <a name="programming-with-the-uml-api"></a>Programming with the UML API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 UML API 進行程式設計](https://docs.microsoft.com/visualstudio/modeling/programming-with-the-uml-api)。  
  
UML API 的 Visual Studio 可讓您撰寫程式碼來建立、 讀取和更新 UML 模型和圖表。 若要查看哪些版本的 Visual Studio 支援 UML 模型，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 除了應用程式開發介面參考頁面之外，下列主題也會描述應用程式開發介面。  
  
|主題|描述的範例類型和方法|描述的功能|  
|-----------|-----------------------------------------|------------------------|  
|[使用 UML API 巡覽關聯性](../modeling/navigate-relationships-with-the-uml-api.md)|UML 項目及其屬性和關聯。 例如，IElement 及其子系，包含：IClass、IActivity、IUseCase、IComponent、IInteraction、IModel、IPackage|在 Visual Studio 的 UML 模型符合 UML 規格版本 2.1.2，可在取得[UML 資源頁](http://go.microsoft.com/fwlink/?LinkId=160796)。 每一個類型都是一個介面，此介面的名稱與 UML 類型相同，且包含前置詞 "I"。|  
|[在 UML 模型中建立項目和關聯性](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|每一個項目類型都有建立其子項目的方法。|  
|[在圖表上顯示 UML 模型](../modeling/display-a-uml-model-on-diagrams.md)|IShape、IDiagram<br /><br /> IShape.Move()|模型中的每一個項目都可做為圖表上的圖形表示。 在某些情況下，您可以為每一個物件建立新圖形。 您可以移動圖形、調整圖形大小、為圖形上色，以及摺疊或展開這些圖形。|  
|[巡覽 UML 模型](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|「模型存放區」可儲存模型。<br /><br /> 「圖表內容」可讓您存取目前的圖表和存放區。|  
|[使用異動連結 UML 模型更新](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|您可以將一系列變更連結到一項異動中。|  
|[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|您可以藉由按兩下或拖曳至圖表之方式定義叫用的命令，藉此擴充圖表的功能。|  
|[定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|您可以定義驗證規則，有助於確保模型符合指定的條件約束。|  
|[從 IDataObject 取得 UML 模型項目](../modeling/get-uml-model-elements-from-idataobject.md)|IElement、IShape|從 [UML 模型總管] 或 UML 圖表將項目拖曳至另一個圖表或應用程式時，該項目會序列化為 IDataObject。|  
|[使用 UML API 編輯 UML 順序圖表](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction、ILifeline、IMessage|建立和更新互動圖表與使用其他圖表類型有些許差異。|  
|[擴充分層圖](../modeling/extend-layer-diagrams.md)|ILayer、ILayerDiagram|您可以撰寫程式碼以建立和編輯分層圖，也可以根據分層圖來驗證程式碼。|  
  
## <a name="about-the-implementation"></a>關於此實作  
 UML 模型工具建置於 [!INCLUDE[dsl](../includes/dsl-md.md)] 上。 每個套件與每個圖表都會以一個 [!INCLUDE[dsl](../includes/dsl-md.md)] 模型來表示，且會維護規則與其他方法的集合之間的一致性。  
  
 來自該平台的類型會顯示在可供您參考以撰寫 UML 擴充功能的某些組件上。 雖然您可以存取 [!INCLUDE[dsl](../includes/dsl-md.md)] 應用程式開發介面以擴充 UML 工具，但您應注意下列事項：  
  
-   您可能會發現有些明顯的簡單變更會導致不一致的情況與未預期的影響。  
  
-   實作方式日後可能會有所變更，而使您透過 [!INCLUDE[dsl](../includes/dsl-md.md)] 應用程式開發介面所做的修改不再適用。  
  
## <a name="the-api-assemblies"></a>應用程式開發介面組件  
 下表摘錄了可為 UML 工具提供擴充性的組件，以及建議您使用的命名空間。  
  
|組件|命名空間|提供存取權給：|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(全部)|UML 類型。|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[建立方法](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[圖表和圖形](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[模型專案](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[版本]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[功能表命令擴充功能](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。<br /><br /> [連結的復原異動](../modeling/link-uml-model-updates-by-using-transactions.md)。|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[驗證](../modeling/define-validation-constraints-for-uml-models.md)|  
||(其他命名空間)|建議僅供進階使用。|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[版本]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)。|  
||(其他命名空間)|建議僅供進階使用。|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[工作項目的連結](../modeling/define-a-work-item-link-handler.md)。|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[工作項目和其欄位](../modeling/define-a-work-item-link-handler.md)。|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[工作項目和其欄位](../modeling/define-a-work-item-link-handler.md)。|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[匯出和匯入的 MEF 元件](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[集合，尤其是處理關聯性的簡易操控](../modeling/navigate-relationships-with-the-uml-api.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)   
 [UML 模型擴充性的 API 參考](../modeling/api-reference-for-uml-modeling-extensibility.md)



