---
title: "建立多個執行個體工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "多重"
  - "工具視窗"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 建立多個執行個體工具視窗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以程式設計的工具視窗，讓多個執行個體可以同時開啟。 根據預設，工具視窗都可以有只有一個開啟的執行個體。  
  
 當您使用多個執行個體工具視窗時，您可以顯示數個相關的資訊來源一次。 例如，您可以將多行 <xref:System.Windows.Forms.TextBox> 控制多個執行個體工具視窗中，這樣一來，程式設計的工作階段期間會同時使用數個程式碼片段。 也比方說，您可以將放 <xref:System.Windows.Forms.DataGrid> 控制項和下拉式清單方塊的多個執行個體工具視窗中，如此可同時追蹤多個即時資料來源。  
  
## 建立基本 （單一執行個體） 的工具視窗  
  
1.  建立專案，名為 **MultiInstanceToolWindow** 使用 VSIX 的範本，並新增名為的自訂工具視窗項目範本 **MIToolWindow**。  
  
    > [!NOTE]
    >  如需使用工具視窗建立擴充功能的詳細資訊，請參閱 [建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## 工具視窗多執行個體  
  
1.  開啟 **MIToolWindowPackage.cs** 檔案並尋找 `ProvideToolWindow` 屬性。 而 `MultiInstances=true` 參數，如下列範例所示。  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  在 MIToolWindowCommand.cs 檔案中，尋找 ShowToolWindos\(\) 方法。 在這種方法，呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並設定其 `create` 旗標設為 `false` ，因此它會逐一查看現有的工具視窗執行個體才可以使用 `id` 找到。  
  
3.  若要建立工具視窗執行個體，呼叫 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法，並設定其 `id` 可用的值和其 `create` 旗標設為 `true`。  
  
     根據預設，值 `id` 參數 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 方法是 `0`。 這可讓單一執行個體工具視窗。 對於裝載的多個執行個體，每個執行個體必須要有它自己唯一 `id`。  
  
4.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 所傳回的物件 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> 工具視窗執行個體的屬性。  
  
5.  根據預設， `ShowToolWindow` 方法所建立的工具視窗項目範本建立的單一執行個體工具視窗。 下列範例顯示如何修改 `ShowToolWindow` 方法來建立多個執行個體。  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```