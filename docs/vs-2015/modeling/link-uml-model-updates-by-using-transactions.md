---
title: 使用異動連結 UML 模型更新 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 640217b9ee9a8cb51ed11931d0d66b2c98e0a165
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945863"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>使用異動連結 UML 模型更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您定義 UML 設計工具在 Visual Studio 中的延伸模組時，您可以數個變更分組到單一異動，稱為*連結的復原內容*。 若要查看哪些 Visual Studio 版本支援 UML 模型，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
 根據預設，您對模型進行的每項修改都可以由使用者分別復原。 例如，如果您定義功能表命令，其交換兩個 UML 類別的名稱，則使用者可以叫用該命令，然後執行單一復原。 這樣會復原對一個名稱的變更，而不會復原其他名稱的變更，從而使模型處於非預期的狀態。  
  
 若要避免此情況，您的程式碼可以在異動內執行一系列變更。 這樣對使用者來說，多個變更就像是單一變更。 後續復原命令會復原這整個系列。  
  
 另外一項益處是程式碼還可以擲回例外狀況或中止此異動，來復原部分完成的一組變更。  
  
## <a name="to-group-changes-into-a-single-transaction"></a>將變更群組為單一異動  
 請確保您的專案參考包含這個 .NET 組件：  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version].dll**  
  
 請在您的類別中宣告具有 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> 類型的已匯入屬性：  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 在修改此模型的方法中，將您的變更置於異動之內：  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 請注意以下各點：  
  
-   您必須一律將 `Commit()` 包含於此異動的結尾。 如果在沒有得到認可的情況下處置異動，則會復原該異動。 也就是說，該模型會還原至此異動開始時的狀態。  
  
-   如果異動內沒有攔截到的例外狀況發生，則會復原該異動。 常見的模式是將異動的 `using` 區塊置於 `try…catch` 區塊內。  
  
-   您可以進行巢狀異動。  
  
-   您可以為 `BeginTransaction()` 提供任何非空白名稱。  
  
-   只有該「UML 模型存放區」會受這些異動影響。 模型異動並不會影響變數、外部存放區 (例如檔案和資料庫)、分層圖和程式碼模型。  
  
## <a name="example"></a>範例  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用 UML API 進行程式設計](../modeling/programming-with-the-uml-api.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [擴充 UML 模型和圖表](../modeling/extend-uml-models-and-diagrams.md)
