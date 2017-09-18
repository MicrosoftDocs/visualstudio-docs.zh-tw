---
title: "使用 VSPackage 建立擴充功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# 使用 VSPackage 建立擴充功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說會示範如何建立 VSIX 專案，並加入 VSPackage 專案項目。 我們將取得以顯示訊息方塊的 UI 殼層服務使用 VSPackage。  
  
## 必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## 建立 VSPackage  
  
1.  建立 VSIX 專案，名為 **FirstPackage**。 您可以找到 VSIX 專案範本，在 **新的專案** 下的對話方塊 **Visual C\# \/ 擴充性**。  
  
2.  專案開啟時，加入名為的 Visual Studio 封裝項目範本 **FirstPackage**。 在 **方案總管\] 中**, ，以滑鼠右鍵按一下專案節點，然後選取 **加入 \/ 新的項目**。 在 **加入新項目** \] 對話方塊中，移至 **Visual C\# \/ 擴充性** ，然後選取 **Visual Studio 套件**。 在 **名稱** 視窗的底部欄位中，將命令檔名稱變更為 **FirstPackage.cs**。  
  
3.  建置此專案並開始偵錯。  
  
     Visual Studio 的實驗執行個體隨即出現。 如需詳細的實驗執行個體的詳細資訊，請參閱 [實驗執行個體](../extensibility/the-experimental-instance.md)。  
  
4.  在實驗執行個體中，開啟 **工具 \/ 擴充功能和更新** 視窗。 您應該會看到 **FirstPackage** 這裡延伸模組。 \(如果您開啟 **擴充功能和更新** 在 Visual Studio 的工作執行個體，不會看到 **FirstPackage**\)。  
  
## 載入 VSPackage  
 此時延伸模組未載入，因為其中沒有任何會導致它載入。 \(按一下功能表命令，開啟 \[工具\] 視窗\)，其 ui 或藉由指定特定 UI 的內容中，應該載入 VSPackage 互動時，您通常可以載入擴充功能。 如需載入 Vspackage 和 UI 內容的詳細資訊，請參閱 [載入 Vspackage](../extensibility/loading-vspackages.md)。 此程序，顯示將如何開啟方案時，載入 VSPackage。  
  
1.  開啟 FirstPackage.cs 檔案。 尋找 FirstPackage 類別的宣告。 以下列取代現有的屬性:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  讓我們加入訊息，讓我們知道已載入 VSPackage。 我們使用 VSPackage initialize \(\) 方法，這樣做，因為 VSPackage 已決定位置之後，才可以取得 Visual Studio 服務。 \(如需取得服務的詳細資訊，請參閱 [如何: 取得服務](../Topic/How%20to:%20Get%20a%20Service.md)。\) 使用取得的程式碼取代 initialize \(\) 方法 FirstPackage 的 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務，取得 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，並呼叫其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> 方法。  
  
    ```c#  
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
  
4.  在實驗執行個體中開啟方案。 您應該會看到訊息方塊，指出 **第一個封裝內 initialize \(\)**。