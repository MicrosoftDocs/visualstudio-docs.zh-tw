---
title: 使用 Visual Studio API 開啟 UML 模型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b492f7c7bcb1c6b33ee7f07b1f054027057835aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490895"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>使用 Visual Studio API 開啟 UML 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 Visual Studio API 開啟 UML 模型](https://docs.microsoft.com/visualstudio/modeling/open-a-uml-model-by-using-the-visual-studio-api)。  
  
您也可以使用 API，在 Visual Studio 使用者介面中開啟模型和圖表。  
  
 如果您只想要讀取程式碼中的模型，而不讓使用者看到它，則可以使用下列方法：  
  
-   Visual Studio 模型匯流排可讓您存取模型和其內的項目，並提供在兩個模型之間建立連結的標準方法。 如需詳細資訊，請參閱 <<c0> [ 整合 UML 模型與其他模型及工具](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  
  
-   您可以使用唯讀模式開啟模型。 如需詳細資訊，請參閱 <<c0> [ 讀取程式碼中的 UML 模型](../modeling/read-a-uml-model-in-program-code.md)。  
  
##  <a name="Showing"></a> 在 Visual Studio 中開啟模型和圖表  
 若要在使用者介面中開啟模型，請使用標準 Visual Studio API `EnvDTE.DTE`。 有兩個您可以針對模型專案項目執行的實用轉換：  
  
-   如果專案是模型專案，以及在目前 AppDomain 中載入專案，則 `EnvDTE.Project` 可以轉換為 `IModelingProject`，以及從中進行轉換。  
  
-   如果項目是 UML 圖表，則 `EnvDTE.ProjectItem` 可以轉換為 `IDiagramContext`，以及從中進行轉換。  
  
 在下列範例中，您的專案應該匯入這些參考：  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
-   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
-   Microsoft.VisualStudio.Shell.Immutable.[version]  
  
-   Microsoft.VisualStudio.Uml.Interfaces  
  
-   System.ComponentModel.Composition  
  
 這個範例會在 Visual Studio 中開啟 UML 模型：  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 在 Visual Studio 延伸模組中，您可以進行這項宣告，以存取主機服務提供者：  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 在方法中，您可以存取專案 (例如，目前專案)：  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)   
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)



