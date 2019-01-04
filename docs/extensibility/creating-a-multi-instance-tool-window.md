---
title: 建立多個執行個體工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1c8652531379d880d44622a4f896f5a30151cdc5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860348"
---
# <a name="create-a-multi-instance-tool-window"></a>建立多個執行個體工具視窗
您可以程式設計的工具視窗，讓多個執行個體可以同時開啟。 根據預設，工具視窗可以有開啟的只有一個執行個體。  
  
 當您使用多重執行個體工具視窗時，您可以顯示在相同的時間資訊的數個相關的來源。 例如，您可以將多行放<xref:System.Windows.Forms.TextBox>控制的多重執行個體工具視窗中，以便在程式設計的工作階段期間會同時提供數個程式碼片段。 此外，比方說，您可以將放入<xref:System.Windows.Forms.DataGrid>控制項和下拉式清單方塊的多重執行個體工具視窗中，如此可以同時追蹤多個即時資料來源。  
  
## <a name="create-a-basic-single-instance-tool-window"></a>建立基本 （單一執行個體） 的工具視窗  
  
1.  建立專案，名為**MultiInstanceToolWindow**使用 [VSIX] 範本，然後新增名為的自訂工具視窗項目範本**MIToolWindow**。  
  
    > [!NOTE]
    >  如需使用工具視窗建立擴充功能的詳細資訊，請參閱[建立的擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="make-a-tool-window-multi-instance"></a>讓工具視窗多重執行個體  
  
1.  開啟*MIToolWindowPackage.cs*檔案，並尋找`ProvideToolWindow`屬性。 和`MultiInstances=true`參數，如下列範例所示：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  在  *MIToolWindowCommand.cs*檔案中，尋找`ShowToolWindos()`方法。 在這種方法，呼叫<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法，並設定其`create`旗標設為`false`，因此它會逐一查看現有的工具視窗中執行個體之前可用`id`找到。  
  
3.  若要建立的工具視窗中執行個體，呼叫<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法，並設定其`id`可用的值並將其`create`旗標設為`true`。  
  
     根據預設，windows 7`id`的參數<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法是`0`。 此值可讓單一執行個體工具視窗。 裝載一個以上的執行個體，每個執行個體必須有自己的唯一`id`。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>所傳回的物件<xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>工具視窗中執行個體的屬性。  
  
5.  根據預設，`ShowToolWindow`方法所建立的工具視窗項目範本建立單一執行個體工具視窗。 下列範例示範如何修改`ShowToolWindow`方法用來建立多個執行個體。  
  
    ```csharp  
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