---
title: "逐步解說：建置應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d24a8b0cfa54b56808e8d283534e03e607fca0c9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-building-an-application"></a>逐步解說：建置應用程式

藉由完成本逐步解說，您將更熟悉使用 Visual Studio 建置應用程式時可設定的幾個選項。 您將針對一個範例應用程式建立自訂組建組態、隱藏特定警告訊息以及增加組建輸出資訊。

## <a name="install-the-sample-application"></a>安裝範例應用程式

下載 [Introduction to Building WPF Applications](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) (組建 WPF 應用程式簡介) 範例。 選擇 C# 或 Visual Basic。 下載 .zip 檔案之後，將它解壓縮，並使用 Visual Studio 開啟 **ExpenseItIntro.sln** 檔案。

## <a name="create-a-custom-build-configuration"></a>建立自訂組建組態

當您建立方案時，系統會自動為方案定義偵錯和發行組建組態以及其預設平台目標。 之後，您可以自訂這些組態或建立您自己的組態。 組建組態指定組建類型。 組建平台指定應用程式針對該組態的目標作業系統。 如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)、[了解組建平台](../ide/understanding-build-platforms.md)和[如何：設定偵錯和發行專案組態](../debugger/how-to-set-debug-and-release-configurations.md)。

您可以使用 [組態管理員] 對話方塊變更或建立組態和平台設定。 在此程序中，您將建立要測試的組建組態。

### <a name="to-create-a-build-configuration"></a>建立組建組態
  
1.開啟 [組態管理員] 對話方塊。
  
     ![Build menu, Configuration Manager command](../ide/media/buildwalk_configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")  
  
2.在 [使用中的方案組態] 清單中，選擇 [\<新增\>]。
  
3.在 [新增方案組態] 對話方塊中，將新的組態命名為 `Test`，從現有的偵錯組態複製設定，然後選擇 [確定] 按鈕。
  
     ![New Solution Configuration Dialog Box](../ide/media/buildwalk_newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")  
  
4.在 [使用中的方案平台] 清單中，選擇 [\<新增\>]。
  
5.在 [新增方案平台] 對話方塊中，選擇 [x64]，而且不要從 x86 平台複製設定。
  
     ![New Solution Platform Dialog Box](../ide/media/buildwalk_newsolutionplatform.png "BuildWalk_NewSolutionPlatform")  
  
6.選擇 [確定] 按鈕。
  
 使用中的方案組態已變更為 [測試]，且使用中的方案平台設定為 [x64]。
  
 ![包含測試組態的 [組態管理員]](../ide/media/buildwalk_configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")  
  
7. 選擇 [關閉]。

您可以使用 [標準] 工具列上的 [方案組態] 清單，快速驗證或變更使用中的方案組態。
  
![[標準] 工具列的 [方案組態] 選項](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")  
  
## <a name="build-the-application"></a>建置應用程式

接下來，您將使用自訂組建組態來建置方案。
  
### <a name="to-build-the-solution"></a>若要建置方案
  
-   在功能表列上，選擇 [建置] 、[建置方案] 。
  
    [輸出] 視窗顯示組建的結果。 組建成功。
  
## <a name="hide-compiler-warnings"></a>隱藏編譯器警告

接下來，我們會介紹一些程式碼，讓編譯器產生警告。

1. 在 C# 專案中，開啟 **ExpenseReportPage.xaml.cs** 檔案。 在 **ExpenseReportPage** 方法中，新增下列程式碼：`int i;`。

    OR

    在 Visual Basic 專案中，開啟 **ExpenseReportPage.xaml.vb** 檔案。 在自訂的建構函式 **Public Sub New...** 中，新增下列程式碼：`Dim i`。

2. 建置方案。

[輸出] 視窗顯示組建的結果。 組建成功，但會產生警告：  

 圖 1：Visual Basic 警告  
  
 ![Visual Basic 輸出視窗](../ide/media/buildwalk_vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")  
  
 圖 2：C# 警告  
  
 ![Visual C&#35; 輸出視窗](../ide/media/buildwalk_csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")  
  
您可以在建置期間暫時隱藏特定警告訊息，以避免干擾建置輸出。

### <a name="to-hide-a-specific-c-warning"></a>隱藏特定 C# 警告
  
1.在 [方案總管]中，選擇頂層專案節點。
  
2.在功能表列上選擇 [檢視]、[屬性頁]。
  
     The **Project Designer** opens.
  
3.選擇 [組建] 頁面，然後在 [隱藏警告] 方塊中指定警告編號 **0168**。
  
     ![Build page, Project Designer](../ide/media/buildwalk_csharpsupresswarnings.png "BuildWalk_CsharpSupressWarnings")  
  
     For more information, see [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).
  
4.建置方案。
  
     The **Output** window displays only summary information for the build.
  
     ![Output Window, Visual C&#35; Build Warnings](../ide/media/buildwalk_visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")  
  
### <a name="to-suppress-all-visual-basic-build-warnings"></a>隱藏所有 Visual Basic 建置警告
  
1.在 [方案總管]中，選擇頂層專案節點。
  
2.在功能表列上選擇 [檢視]、[屬性頁]。
  
     The **Project Designer** opens.
  
3.在 [編譯] 頁面上，選取 [停用所有警告] 核取方塊。
  
     ![Compile page, Project Designer](../ide/media/buildwalk_vbsupresswarnings.png "BuildWalk_VBSupressWarnings")  
  
     For more information, see [Configuring Warnings in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).
  
4.建置方案。
  
 [輸出] 視窗只會顯示組建的摘要資訊。
  
 ![輸出視窗、Visual Basic 建置警告](../ide/media/buildwalk_visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")  
  
 如需詳細資訊，請參閱[如何︰隱藏編譯器警告](../ide/how-to-suppress-compiler-warnings.md)。
  
## <a name="display-additional-build-details-in-the-output-window"></a>在輸出視窗中顯示其他組建詳細資料

您可以變更出現在 [輸出] 視窗中的建置流程相關資訊量。 建置詳細等級通常會設定為 [最小]，這表示 [輸出] 視窗只會顯示建置流程摘要，以及任何高優先順序警告或錯誤。 您可以使用[選項對話方塊、專案和方案、建置並執行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)，來顯示有關組建的詳細資訊。
  
> [!IMPORTANT]
>  如果顯示詳細資訊，組建將需要更長的時間來完成。
  
### <a name="to-change-the-amount-of-information-in-the-output-window"></a>變更輸出視窗中的資訊量
  
1.開啟 [選項] 對話方塊。
  
     ![Options command on the Tools menu](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-ToolsOptionsmenu")  
  
2.選擇 [專案和方案] 分類，然後選擇 [建置並執行] 頁面。
  
3.在 [MSBuild 專案建置輸出詳細等級] 清單中，選擇 [一般]，然後選擇 [確定] 按鈕。
  
4.在功能表列上，選擇 [建置]、[清除方案]。
  
5.建置方案，然後檢閱 [輸出] 視窗中的資訊。
  
     The build information includes the time that the build started (located at the beginning) and the order in which files were processed. This information also includes the actual compiler syntax that Visual Studio runs during the build.
  
     For example, in the C# build, the [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) option lists the warning code, 1762, that you specified earlier in this topic, along with three other warnings.
  
     In the Visual Basic build, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) doesn't include specific warnings to exclude, so no warnings appear.
  
    > [!TIP]
    >  You can search the contents of the **Output** window if you display the **Find** dialog box by choosing the Ctrl+F keys.
  
如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。
  
## <a name="create-a-release-build"></a>建立發行組建

您可以建置已針對交付最佳化的範例應用程式版本。 針對發行組建，您將指定在開始建置之前將可執行檔複製到網路共用。

如需詳細資訊，請參閱[如何：變更建置輸出目錄](../ide/how-to-change-the-build-output-directory.md)和[在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)。

### <a name="to-specify-a-release-build-for-visual-basic"></a>指定 Visual Basic 的發行組建
  
1.開啟 [專案設計工具]。
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.選擇 [編譯] 頁面。
  
3.在 [組態] 清單中，選擇 [發行]。
  
4.在 [平台] 清單中，選擇 [x86]。
  
5.在 [建置輸出路徑] 方塊中，指定網路路徑。
  
     For example, you can specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6.建置應用程式。
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
### <a name="to-specify-a-release-build-for-c"></a>指定 C# 的發行組建 #
  
1.開啟 [專案設計工具]。
  
     ![View menu, Property Pages command](../ide/media/buildwalk_viewpropertypages.png "BuildWalk_ViewPropertyPages")  
  
2.選擇 [組建] 頁面。
  
3.在 [組態] 清單中，選擇 [發行]。
  
4.在 [平台] 清單中，選擇 [x86]。
  
5.在 [輸出路徑] 方塊中，指定網路路徑。
  
     For example, you could specify \\\myserver\builds.
  
    > [!IMPORTANT]
    >  A message box might appear, warning you that the network share that you've specified might not be a trusted location. If you trust the location that you've specified, choose the **OK** button in the message box.
  
6.在 [標準] 工具列上，將 [方案組態] 設定為 [發行]，[方案平台] 設定為 [x86]。

7.建置應用程式。
  
     ![Build Solution command on the Build menu](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
 可執行檔會複製到您指定的網路路徑。 其路徑為 \\\myserver\builds\\<檔名>.exe。
  
恭喜︰您已成功完成本逐步解說。
  
## <a name="see-also"></a>另請參閱

[逐步解說：建置專案 (C++)](/cpp/ide/walkthrough-building-a-project-cpp)  
[ASP.NET Web 應用程式專案先行編譯概觀](http://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)  
[逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)
