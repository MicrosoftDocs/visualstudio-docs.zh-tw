---
title: "建立 VSPackage 擴充功能 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: df971bdf72ff52cfa6343b6237de072238087ac4
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="creating-an-extension-with-a-vspackage"></a>建立 VSPackage 擴充功能
本逐步解說將示範如何建立 VSIX 專案，並加入 VSPackage 專案項目。 我們將使用 VSPackage 來取得 UI Shell 服務才能顯示訊息方塊。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-a-vspackage"></a>建立 VSPackage  
  
1.  建立 VSIX 專案，名為**FirstPackage**。 您可以找到 VSIX 專案範本，在**新專案**對話方塊底下**Visual C# / 擴充性**。  
  
2.  當專案開啟時，加入名為的 Visual Studio 封裝項目範本**FirstPackage**。 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在**加入新項目**對話方塊中，移至**Visual C# / 擴充性**選取**Visual Studio Package**。 在**名稱**視窗的底部欄位中，將命令檔名稱變更為**FirstPackage.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需實驗執行個體的詳細資訊，請參閱[實驗執行個體的](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，開啟**工具 / 擴充功能和更新**視窗。 您應該會看到**FirstPackage**這裡擴充功能。 (如果您開啟**擴充功能和更新**在 Visual Studio 工作執行個體，您將不會看到**FirstPackage**)。  
  
## <a name="loading-the-vspackage"></a>載入 VSPackage  
 此時擴充功能無法載入，因為沒有與載入它的項目。 （按一下開啟工具視窗的功能表命令），其 UI 或藉由指定特定 UI 內容中，應該載入 VSPackage 互動時，您通常可以載入擴充功能。 如需載入 Vspackage 和 UI 內容的詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。 在此程序，我們將示範如何載入 VSPackage，開啟方案時。  
  
1.  開啟 FirstPackage.cs 檔案。 尋找 FirstPackage 類別的宣告。 以下列取代現有的屬性：  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  讓我們加入可讓我們知道已載入 VSPackage 的訊息。 我們使用 VSPackage 的 initialize （） 方法若要這樣做，因為只有之後已設置 VSPackage，您可以取得 Visual Studio 服務。 (如需取得服務的詳細資訊，請參閱[How to： 取得服務](../extensibility/how-to-get-a-service.md)。)FirstPackage initialize （） 方法取代程式碼可取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務，取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面，並呼叫其<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>方法。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
4.  在實驗執行個體中開啟方案。 您應該會看到訊息方塊，表示**initialize 內第一個套件**。