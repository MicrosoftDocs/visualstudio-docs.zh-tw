---
title: 逐步解說：建置應用程式
description: 更熟悉您在使用 Visual Studio 建立應用程式時可以設定的數個選項。
ms.custom: SEO-VS-2020
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7fe40f78b8a8447c1ae784e33a25e905e368118
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873823"
---
# <a name="walkthrough-build-an-application"></a>逐步解說：建置應用程式

藉由完成本逐步解說，您將更熟悉使用 Visual Studio 建置應用程式時可設定的幾個選項。 您將針對一個範例應用程式建立自訂組建組態、隱藏特定警告訊息以及增加組建輸出資訊。

## <a name="install-the-sample-application"></a>安裝範例應用程式

下載 [Introduction to building WPF applications](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) (組建 WPF 應用程式簡介) 範例。 選擇 C# 或 Visual Basic。 下載 *.zip* 檔案之後，將它解壓縮，並使用 Visual Studio 開啟 *ExpenseItIntro.sln* 檔案。

## <a name="create-a-custom-build-configuration"></a>建立自訂組建組態

當您建立方案時，系統會自動為方案定義偵錯和發行組建組態以及其預設平台目標。 之後，您可以自訂這些組態或建立您自己的組態。 組建組態指定組建類型。 組建平台指定應用程式針對該組態的目標作業系統。 如需詳細資訊，請參閱[了解組建組態](../ide/understanding-build-configurations.md)、[了解組建平台](../ide/understanding-build-platforms.md)和[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。

您可以使用 [組態管理員] 對話方塊變更或建立組態和平台設定。 在此程序中，您將建立要測試的組建組態。

### <a name="create-a-build-configuration"></a>建立組建組態

1. 開啟 [組態管理員] 對話方塊。

   ![[組態管理員] 命令、[建置] 功能表](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. 在 [使用中的 **方案** 設定] 清單中，選擇 [] **\<New...\>** 。

1. 在 [新增方案組態] 對話方塊中，將新的組態命名為 `Test`，從現有的 [偵錯] 組態複製設定，然後選擇 [確定] 按鈕。

   ![[新增方案組態] 對話方塊](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. 在 [使用中的 **方案平臺** ] 清單中，選擇 [] **\<New...\>** 。

1. 在 [新增方案平台] 對話方塊中，選擇 [x64]，而不要從 x86 平台複製設定。

   ![[新增方案平台] 對話方塊](../ide/media/buildwalk_newsolutionplatform.png)

1. 選擇 [確定]  按鈕。

   使用中的方案組態已變更為 [測試]，且使用中的方案平台設定為 x64。

   ![包含測試組態的 [組態管理員]](../ide/media/buildwalk_configmanagertestconfig.png)

1. 選擇 [關閉]。

您可以使用 [標準] 工具列上的 [方案組態] 清單，快速驗證或變更使用中的方案組態。

![方案組態選項標準工具列](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>建置應用程式

接下來，您將使用自訂組建組態來建置方案。

### <a name="build-the-solution"></a>建立解決方案

- 在功能表列上，選擇 [**組建**  >  **組建方案**] 或按 **Ctrl** + **Shift** + **B**。

    [輸出] 視窗顯示組建的結果。 組建成功。

## <a name="hide-compiler-warnings"></a>隱藏編譯器警告

接下來，我們會介紹一些程式碼，讓編譯器產生警告。

1. 在 C# 專案中，開啟 *ExpenseReportPage.xaml.cs* 檔案。 在 **ExpenseReportPage** 方法中，新增下列程式碼：`int i;`。

    OR

    在 Visual Basic 專案中，開啟 *ExpenseReportPage.xaml.vb* 檔案。 在自訂的建構函式 **Public Sub New...** 中，新增下列程式碼：`Dim i`。

1. 建置方案。

[輸出] 視窗顯示組建的結果。 組建成功，但會產生警告：

![輸出視窗 Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![輸出視窗 Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

您可以在建置期間暫時隱藏特定警告訊息，以避免干擾建置輸出。

### <a name="hide-a-specific-c-warning"></a>隱藏特定 C# 警告

1. 在 **方案總管** 中，選擇頂層專案節點。

1. 在功能表列上，選擇 [ **View**  >  **Property Pages**]。

     [專案設計工具] 隨即開啟。

1. 選擇 [組建] 頁面，然後在 [隱藏警告] 方塊中指定警告編號 **0168**。

     ![專案設計工具、建置頁](../ide/media/buildwalk_csharpsuppresswarnings.png)

     如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](../ide/reference/build-page-project-designer-csharp.md)。

1. 建置方案。

     [輸出] 視窗只會顯示組建的摘要資訊。

     ![Visual C&#35; 建置警告、輸出視窗](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>隱藏所有 Visual Basic 建置警告

1. 在 **方案總管** 中，選擇頂層專案節點。

2. 在功能表列上，選擇 [ **View**  >  **Property Pages**]。

     [專案設計工具] 隨即開啟。

3. 在 [編譯] 頁面上，選取 [停用所有警告] 核取方塊。

     ![專案設計工具、編譯頁](../ide/media/buildwalk_vbsuppresswarnings.png)

     如需詳細資訊，請參閱[在 Visual Basic 中設定警告](../ide/configuring-warnings-in-visual-basic.md)。

4. 建置方案。

   [輸出] 視窗只會顯示組建的摘要資訊。

   ![Visual Basic 建置警告、輸出視窗](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   如需詳細資訊，請參閱[如何︰隱藏編譯器警告](../ide/how-to-suppress-compiler-warnings.md)。

## <a name="display-additional-build-details-in-the-output-window"></a>在輸出視窗中顯示其他組建詳細資料

您可以變更出現在 [輸出] 視窗中的建置流程相關資訊量。 建置詳細等級通常會設定為 [最小]，這表示 [輸出] 視窗只會顯示建置流程摘要，以及任何高優先順序警告或錯誤。 您可以使用[選項對話方塊、專案和方案、建置並執行](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)，來顯示組建的詳細資訊。

> [!IMPORTANT]
> 如果顯示詳細資訊，組建將需要更長的時間來完成。

### <a name="change-the-amount-of-information-in-the-output-window"></a>變更輸出視窗中的資訊量

1. 開啟 [選項] 對話方塊。

     ![[工具] 功能表上的 [選項] 命令](../ide/media/exploreide-toolsoptionsmenu.png)

1. 選擇 [專案和方案] 分類，然後選擇 [建置並執行] 頁面。

1. 在 [MSBuild 專案建置輸出詳細等級] 清單中，選擇 [一般]，然後選擇 [確定] 按鈕。

1. 在功能表列上，選擇 [**建立**  >  **全新方案**]。

1. 建置方案，然後檢閱 [輸出] 視窗中的資訊。

     組建資訊包含組建的開始時間 (位於開頭) 以及檔案的處理順序。 這項資訊也包含 Visual Studio 在建置期間執行的實際編譯器語法。

     例如，在 c # 組建中， [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 選項會列出您稍早在本主題中指定的警告碼 **0168**，以及其他三個警告。

     在 Visual Basic 組建中，[/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 不包含要排除的特定警告，因此不會出現任何警告。

    > [!TIP]
    > 如果您選擇 **Ctrl**+**F** 鍵顯示 [尋找] 對話方塊，即可搜尋 [輸出] 視窗的內容。

如需詳細資訊，請參閱[如何：檢閱、儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。

## <a name="create-a-release-build"></a>建立發行組建

您可以建置已針對交付最佳化的範例應用程式版本。 針對發行組建，您將指定在開始建置之前將可執行檔複製到網路共用。

如需詳細資訊，請參閱[如何：變更組建輸出目錄](../ide/how-to-change-the-build-output-directory.md)和[在 Visual Studio 中建置和清除專案與方案](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)。

### <a name="specify-a-release-build-for-visual-basic"></a>指定 Visual Basic 的發行組建

1. 開啟 [專案設計工具]。

     ![[屬性頁] 命令、[檢視] 功能表](../ide/media/buildwalk_viewpropertypages.png)

1. 選擇 [編譯] 頁面。

1. 在 [組態] 清單中，選擇 [發行]。

1. 在 [平台] 清單中，選擇 [x86]。

1. 在 [建置輸出路徑] 方塊中，指定網路路徑。

     例如，您可以指定 `\\myserver\builds`。

    > [!IMPORTANT]
    > 可能會出現一個訊息方塊，警告您所指定的網路共用可能不是信任的位置。 如果您信任所指定的位置，請在訊息方塊中選擇 [確定] 按鈕。

1. 建置應用程式。

     ![[建置] 功能表上的 [建置方案] 命令](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>指定 C\# 的發行組建

1. 開啟 [專案設計工具]。

     ![[屬性頁] 命令、[檢視] 功能表](../ide/media/buildwalk_viewpropertypages.png)

1. 選擇 [組建] 頁面。

1. 在 [組態] 清單中，選擇 [發行]。

1. 在 [平台] 清單中，選擇 [x86]。

1. 在 [輸出路徑] 方塊中，指定網路路徑。

     例如，您可以指定 `\\myserver\builds`。

    > [!IMPORTANT]
    > 可能會出現一個訊息方塊，警告您所指定的網路共用可能不是信任的位置。 如果您信任所指定的位置，請在訊息方塊中選擇 [確定] 按鈕。

1. 在 [標準] 工具列上，將 [方案組態] 設定為 [發行]，[方案平台] 設定為 [x86]。

1. 建置應用程式。

     ![[建置] 功能表上的 [建置方案] 命令](../ide/media/exploreide-buildsolution.png)

   可執行檔會複製到您指定的網路路徑。 其路徑會是 `\\myserver\builds\\FileName.exe`。

恭喜！ 您已經成功完成此逐步解說。

## <a name="see-also"></a>另請參閱

- [逐步解說： (c + + 建立專案) ](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET Web 應用程式專案先行編譯概觀](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [逐步解說：使用 MSBuild](../msbuild/walkthrough-using-msbuild.md)
