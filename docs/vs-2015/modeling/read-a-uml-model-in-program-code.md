---
title: 讀取程式碼中的 UML 模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37539ee6c031d88b9db279cc61214ac5e3077e76
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387674"
---
# <a name="read-a-uml-model-in-program-code"></a>讀取程式碼中的 UML 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以載入 UML 模型和它使用 UML 應用程式開發介面的圖表。  
  
## <a name="Reading"></a> 讀取程式碼中的模型  
 若要存取模型內容，卻不顯示在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 視窗中，請使用 `ModelingProject.LoadReadOnly()`。  
  
 例如:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 如果想要讀取圖表中的圖形，您必須先讀取專案，再讀取圖表。  
  
 例如:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>替代方法  
 對於許多應用程式， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus 可讓您參考模型和元素，以更強固性和彈性比本主題中描述的方法。 它提供在任意項目間建立連結的標準方法，無論其位於相同或不同的模型。 如需詳細資訊，請參閱 <<c0> [ 整合 UML 模型與其他模型及工具](../modeling/integrate-uml-models-with-other-models-and-tools.md)。  
  
 您也可以在使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式開發介面的使用者介面中，開啟模型和圖表。 如需詳細資訊，請參閱 <<c0> [ 使用 Visual Studio API 開啟 UML 模型](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)。  
  
## <a name="Standalone"></a> 獨立應用程式  
 上節中的範例會在 Visual Studio 擴充功能中發揮作用。 在獨立應用程式中讀取模型是可能的，但是您必須在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案中加入一些參考。  
  
> [!NOTE]
> 未來的產品版本可能會變更在獨立應用程式中讀取模型的詳細方式。 未來版本可能不提供目前版本可以存取的某些功能。  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>加入參考以在獨立應用程式中讀取模型。  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下的專案，您要建置的應用程式，然後按一下**屬性**。 在屬性編輯器中，在**應用程式**索引標籤上，設定**目標 Framework**到必要的.NET Framework 版本。  
  
2. 加入存取 UML 模型所需的 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 參考，一般為：  
  
   - Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. 除了先前章節中所列的參考，加入下列專案參考從 **\Program Files\Microsoft Visual Studio [版本] \Common7\IDE\PrivateAssemblies** :  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     如果想要讀取應用程式中的圖表，您可能也需要這些參考：  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>另請參閱  
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)   
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)
