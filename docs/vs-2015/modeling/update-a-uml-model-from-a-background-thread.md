---
title: 更新 UML 模型，從背景執行緒 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 448a24d2bfe7a466a239c025046bd0e6f13ea64e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500465"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>從背景執行緒更新 UML 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[更新 UML 模型，從背景執行緒](https://docs.microsoft.com/visualstudio/modeling/update-a-uml-model-from-a-background-thread)。  
  
有時可能適用於在背景執行緒中變更模型。 例如，如果您是從慢速的外部資源載入資訊，則可以使用背景執行緒來負責更新。 這可讓使用者立即看到可用的更新。  
  
 不過，您必須注意 UML 存放區未具有執行緒安全功能。 下列預防措施十分重要：  
  
-   對模型或圖表進行的每個更新都必須在使用者介面 (UI) 執行緒中進行。 背景執行緒必須使用 <xref:System.Windows.Forms.Control.Invoke%2A> 或 `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A>讓 UI  執行緒執行實際更新。  
  
-   如果您將一系列的變更群組為單一交易，則建議您防止使用者在進行交易時編輯模型。 否則，使用者所做的任何編輯都將成為相同交易的一部分。 透過顯示強制回應對話方塊，即可防止使用者進行變更。 如果想要的話，您可以在對話方塊中提供 [取消] 按鈕。 使用者可以看到發生的變更。  
  
## <a name="example"></a>範例  
 這個範例使用背景執行緒，以對模型進行數項變更。 對話方塊用來在執行執行緒時排除使用者。 在這個簡單的範例中，未在對話方塊中提供任何 [取消] 按鈕。 不過，加入該功能極為容易。  
  
#### <a name="to-run-the-example"></a>執行範例  
  
1.  建立 C# 專案中的命令處理常式，如中所述[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)。  
  
2.  請確定專案包含這些組件的參考：  
  
    -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
    -   Microsoft.VisualStudio.Uml.Interfaces  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
3.  將 Windows 表單名為加入至專案**ProgressForm**。 它應該會顯示一則訊息，而這則訊息指出正在更新。 這不需要有任何其他控制。  
  
4.  加入含有步驟 7 後所顯示程式碼的 C# 檔案。  
  
5.  建置並執行專案。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的新執行個體隨即在實驗模式中啟動。  
  
6.  在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的實驗執行個體中，建立或開啟 UML 類別圖。  
  
7.  以滑鼠右鍵按一下 UML 類別圖的任何位置，然後按一下**新增數個 UML 類別**。  
  
 數個新的類別方塊會出現在圖表中，並以半秒的間隔逐一出現。  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>允許使用者取消範例中的執行緒  
  
1.  在 [進度] 對話方塊中加入 [取消] 按鈕。  
  
2.  將下列程式碼加入 [進度] 對話方塊：  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  在 Execute() 方法中，於建構表單之後插入下列一行：  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>存取 UI 執行緒的其他方法  
 如果您不想要建立對話方塊，則可以存取可顯示圖表的控制項：  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 您可以使用 `uiThreadHolder.Invoke()`，在 UI 執行緒中執行作業。  
  
## <a name="see-also"></a>另請參閱  
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [在模型圖表上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)



