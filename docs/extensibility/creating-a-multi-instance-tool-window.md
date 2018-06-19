---
title: 建立多個執行個體工具視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 910ca8f223d5f4f37242990ba7384afb0dbebd7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31097792"
---
# <a name="creating-a-multi-instance-tool-window"></a>建立多個執行個體工具視窗
您可以在使多個執行個體可以同時開啟程式的工具視窗。 根據預設，工具視窗可以有只有一個執行個體開啟。  
  
 當您使用多個執行個體工具視窗時，您可以顯示數個相關的資訊來源在相同的時間。 例如，您可以將多行<xref:System.Windows.Forms.TextBox>控制多個執行個體工具視窗中，以便程式設計的工作階段期間會同時使用數個程式碼片段。 此外，例如，您無法將<xref:System.Windows.Forms.DataGrid>控制項和下拉式清單方塊中的多個執行個體工具視窗，讓多個即時資料來源可同時追蹤。  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>建立基本 （單一執行個體） 的工具視窗  
  
1.  建立專案，名為**MultiInstanceToolWindow**使用 VSIX 範本，並新增名為的自訂工具視窗項目範本**MIToolWindow**。  
  
    > [!NOTE]
    >  如需使用的工具視窗建立擴充功能的詳細資訊，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="making-a-tool-window-multi-instance"></a>工具視窗多重執行個體  
  
1.  開啟**MIToolWindowPackage.cs**檔案，並尋找`ProvideToolWindow`屬性。 和`MultiInstances=true`參數，如下列範例所示：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  在 MIToolWindowCommand.cs 檔案中，尋找 ShowToolWindos() 方法。 在這種方法，呼叫<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法並將其`create`旗標設為`false`，讓它會逐一查看現有的執行個體工具視窗才可供`id`找到。  
  
3.  若要建立工具視窗執行個體，請呼叫<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法並將其`id`可用的值和其`create`旗標設為`true`。  
  
     根據預設，值`id`參數<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法`0`。 這個值會使單一執行個體工具視窗。 裝載的多個執行個體，每個執行個體必須有自己的唯一`id`。  
  
4.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>所傳回的物件<xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>工具視窗中執行個體的屬性。  
  
5.  根據預設，`ShowToolWindow`方法所建立的工具視窗項目範本建立的單一執行個體工具視窗。 下列範例示範如何修改`ShowToolWindow`方法來建立多個執行個體。  
  
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