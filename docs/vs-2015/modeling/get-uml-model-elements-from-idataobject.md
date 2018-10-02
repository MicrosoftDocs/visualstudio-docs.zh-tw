---
title: 從 IDataObject 取得 UML 模型項目 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a69a6f20fdccdce9d8795c68bf0a70c74604428b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497509"
---
# <a name="get-uml-model-elements-from-idataobject"></a>從 IDataObject 取得 UML 模型項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[從 IDataObject 取得 UML 模型項目](https://docs.microsoft.com/visualstudio/modeling/get-uml-model-elements-from-idataobject)。  
  
當使用者從任何來源拖曳項目到圖表中時，拖曳的項目會編碼於 `System.Windows.Forms.IDataObject`。 編碼取決於來源物件的類型。 下列片段示範當來源是 UML 圖表時，如何擷取項目。  
  
> [!NOTE]
>  可執行的作業，您必須在 UML 模型上執行的大部分使用類型在組件中定義**Microsoft.VisualStudio.Uml.Interfaces**和**Microsoft.VisualStudio.ArchitectureTools.Extensibility**。 但是，基於此目的，您必須使用屬於 UML 模型工具實作一部分的一些類別。 例如，在此片段中的 `ShapeElement` 與 UML  `IShape` 不同。 若要降低使 UML 模型和圖表處於不一致狀態的風險，最好避免對這些實作類別使用方法，除非別無選擇。  
  
## <a name="code-sample"></a>範例程式碼  
 您的專案必須參考下列[!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]組件：  
  
 **Microsoft.VisualStudio.Modeling.Sdk。[版本]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams。[版本]**  
  
 **System.Windows.Forms**  
  
```  
using Microsoft.VisualStudio.Modeling;    
  // for ElementGroupPrototype  
using Microsoft.VisualStudio.Modeling.Diagrams;    
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs  
…   
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
                  (DiagramDragEventArgs dragEvent)  
  {  
     //ElementGroupPrototype is the container for  
     //dragged and copied elements and toolbox items.  
     ElementGroupPrototype prototype =  
        dragEvent.Data.  
        GetData(typeof(ElementGroupPrototype))  
                     as ElementGroupPrototype;  
     // Locate the originals in the implementation store.  
     IElementDirectory implementationDirectory =   
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
     return  prototype.ProtoElements.Select(  
       prototypeElement =>   
       {  
          ModelElement element = implementationDirectory  
                .FindElement(prototypeElement.ElementId);  
          ShapeElement shapeElement = element as ShapeElement;  
          if (shapeElement != null)  
          {   
            // Dragged from a diagram.  
            return shapeElement.ModelElement as IElement;  
          }  
          else  
          {   
            // Dragged from UML Model Explorer.  
            return element as IElement;  
          }  
        });  
    }  
```  
  
 如需詳細資訊`ElementGroupPrototype`而`Store`中的 UML 模型工具實作時，請參閱[Modeling SDK for Visual Studio-特定領域語言](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



