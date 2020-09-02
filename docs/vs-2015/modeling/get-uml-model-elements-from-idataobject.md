---
title: 從 IDataObject 取得 UML 模型元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666082"
---
# <a name="get-uml-model-elements-from-idataobject"></a>從 IDataObject 取得 UML 模型項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當使用者從任何來源拖曳項目到圖表中時，拖曳的項目會編碼於 `System.Windows.Forms.IDataObject`。 編碼取決於來源物件的類型。 下列片段示範當來源是 UML 圖表時，如何擷取項目。

> [!NOTE]
> 您必須對 UML 模型執行的大部分作業都可以使用 **VisualStudio** 元件中所定義的型別，以及 **VisualStudio. [microsoft.visualstudio.architecturetools.layer.validator**擴充性。 但是，基於此目的，您必須使用屬於 UML 模型工具實作一部分的一些類別。 例如，在此片段中的 `ShapeElement` 與 UML  `IShape` 不同。 若要降低使 UML 模型和圖表處於不一致狀態的風險，最好避免對這些實作類別使用方法，除非別無選擇。

## <a name="code-sample"></a>程式碼範例
 您的專案必須參考下列 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] 元件：

 **Microsoft.VisualStudio.Modeling.Sdk.[版本]**

 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[版本]**

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

 如需有關 `ElementGroupPrototype` 的詳細資訊 `Store` ，以及 UML 模型工具的執行方式，請參閱 [Visual Studio 網域專屬語言的模型 SDK](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)。

## <a name="see-also"></a>另請參閱
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)[在模型圖表上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
