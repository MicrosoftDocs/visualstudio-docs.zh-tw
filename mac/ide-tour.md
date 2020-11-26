---
title: Visual Studio for Mac 教學課程
description: Visual Studio for Mac 提供整合式的開發環境，以在 macOS 上建置 .NET 應用程式，包括 ASP.NET Core 網站，和適用於 iOS、Android、Mac 和 Xamarin.Forms 的 Xamarin 專案。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: a2caadd454564b389f48987e69e1bc08475affea
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190183"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Visual Studio 2019 for Mac 導覽

Visual Studio for Mac 是 Mac 上的 _.NET 整合式開發環境_，可用來編輯、偵錯及建置程式碼，然後發佈應用程式。 除了程式碼編輯器和偵錯工具之外，Visual Studio for Mac 還包含編譯器、程式碼完成工具、圖形設計工具和原始檔控制功能，以簡化軟體發展流程。

Visual Studio for Mac 支援的檔案類型很多都與 Windows 相同，例如 `.csproj`、`.fsproj`或 `.sln` 檔案，也支援 EditorConfig 這類功能，也就是說，您可以使用最適合您的 IDE。
建立、開啟及開發應用程式，對於先前在 Windows 上使用 Visual Studio 的任何人而言，將會是熟悉的經驗。 此外，Visual Studio for Mac 採用許多功能強大的工具，這些工具讓其 Windows 對等項目成為功能如此強大的 IDE。 Roslyn 編譯器平台用於重構和 IntelliSense。 它的專案系統和組建引擎使用 MSBuild，而其來源編輯器使用與 Windows 上的 Visual Studio 相同的基礎。 它為 Xamarin 與 .NET Core 應用程式使用相同的偵錯工具引擎，並為 Xamarin.iOS 和 Xamarin.Android 使用相同的設計工具。

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Visual Studio for Mac 內含哪些功能

Visual Studio for Mac 支援下列幾種開發作業：

- 使用 c #、F # 和 Razor pages、JavaScript 和 TypeScript 的支援來 ASP.NET Core web 應用程式
- 使用 C# 或 F# 開發 .NET Core 主控台應用程式
- 使用 C# 開發跨平台 Unity 遊戲和應用程式
- 使用 C# 或 F# 和 XAML 在 Xamarin 中開發 Android、iOS、tvOS 和 watchOS 應用程式
- 使用 C# 或 F# 開發 Cocoa 傳統型應用程式

本文探討 Visual Studio for Mac 的各個部分，提供一些功能的相關資訊，讓它成為建立這些應用程式的強大工具。

## <a name="ide-tour"></a>IDE 導覽

Visual Studio for Mac 分成數個區段，以便管理應用程式檔案和設定、建立應用程式程式碼及偵錯。

## <a name="getting-started"></a>開始使用

當您第一次啟動 Visual Studio 2019 for Mac 時，新的使用者會看到登入視窗。 使用您的 Microsoft 帳戶登入以啟動付費授權 (如果有的話) 或 Azure 訂用帳戶的連結。 您可以按 [稍後]，稍後再透過 **Visual Studio > 登入** 功能表項目 **進行** 登入：

![登入您的 Microsoft 帳戶](media/ide-tour-2019-start-signin.png)

然後，您可以選取慣用的鍵盤快速鍵來自訂 IDE： Visual Studio for Mac、Visual Studio、Visual Studio Code 或 Xcode：

![選取您慣用的鍵盤快速鍵](media/ide-tour-2019-keyboard-shortcut.png)

在此初始設定體驗之後，您會在開啟 Visual Studio 2019 for Mac 時看到 [ _開始] 視窗_ ，其中顯示最近的專案清單，以及開啟現有專案或建立新專案的按鈕：

![從最近使用的專案中選擇，或建立新的專案](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>方案和專案

下圖顯示已載入應用程式的 Visual Studio for Mac：

![已載入應用程式的 Visual Studio for Mac](media/ide-tour-image17.png)

下列各節提供 Visual Studio for Mac 中主要區域的概觀。

## <a name="solution-window"></a>方案視窗

方案視窗會將專案 (的) 組織成方案：

![方案視窗中組織的專案](media/ide-tour-image18.png)

這是原始碼、資源、使用者介面和相依性的檔案組織成平台專屬專案的位置。

如需在 Visual Studio for Mac 中使用專案和方案的詳細資訊，請參閱[專案和方案](./projects-and-solutions.md)一文。

## <a name="assembly-references"></a>組件參考

每個專案的組件參考，提供於 [參考] 資料夾底下：

![方案視窗中的參考資料夾](media/ide-tour-image19.png)

其他參考資料是使用 [編輯參考] 對話方塊來新增，其顯示方法是在 [參考] 資料夾上按兩下，或在其操作功能表動作上選取 [編輯參考]：

![[編輯參考] 對話方塊](media/ide-tour-image20.png)

如需在 Visual Studio for Mac 中使用參考的詳細資訊，請參閱[管理專案中的參考](./managing-references-in-a-project.md)一文。

## <a name="dependencies--packages"></a>相依性 / 封裝

您應用程式中使用的所有外部相依性都會儲存在 [相依性] 或 [套件] 資料夾中，視您是在 .NET Core 或 Xamarin. Android 專案中而定。 這些通常會以 NuGet 的形式提供。

NuGet 是適用於 .NET 開發最受歡迎的套件管理員。 使用 Visual Studio 的 NuGet 支援，您可以輕鬆地搜尋並新增套件至您的應用程式專案。

若要將相依性新增至應用程式，請以滑鼠右鍵按一下 [相依性] / [套件] 資料夾，然後選取 [新增套件]：

![新增 NuGet 套件](media/ide-tour-image21.png)

在應用程式中使用 NuGet 套件的相關資訊，可於[在專案中包含 NuGet 專案](./nuget-walkthrough.md)一文中找到。

## <a name="source-editor"></a>原始檔編輯器

無論您是以 c #、XAML 或 JavaScript 撰寫，程式碼編輯器都會與 Windows 上的 Visual Studio 共用相同的核心元件，並具有完全原生的使用者介面。

這會帶來下列部分功能：

* 原生 macOS (以 Cocoa 為基礎) 使用者介面 (工具提示、編輯器介面、邊界裝飾、文字轉譯、IntelliSense)
* IntelliSense 類型篩選和「顯示匯入專案」
* 原生文字輸入的支援
* RTL/BiDi 語言支援
* Roslyn 3
* 多個插入點的支援
* 自動換行
* 已更新 IntelliSense UI
* 改善的尋找/取代
* 程式碼片段支援 
* 格式選取項目
* 內嵌燈泡

如需在 Visual Studio for Mac 中使用來源編輯器的詳細資訊，請參閱 [原始檔編輯器](./source-editor.md) 檔。

若要隨時保持可用的索引標籤，您可以利用釘選它們。 這可確保每次您啟動專案時，您需要的索引標籤一律會顯示。 若要釘選索引標籤，請將滑鼠停留在索引標籤上，然後按一下 _釘_ 選圖示

![釘選索引標籤](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>重構

Visual Studio for Mac 提供兩種有用的方式來重構程式碼：內容動作和原始檔分析。 您可以在[重構](./refactoring.md)一文中閱讀有關它們的深入資訊。

## <a name="debugging"></a>偵錯

Visual Studio for Mac 具有可支援 .NET Core、.NET Framework、Unity 和 Xamarin 專案的偵錯工具。 Visual Studio for Mac 使用 .NET Core 偵錯工具和 Mono 軟偵錯工具，可讓 IDE 在所有平臺上進行 managed 程式碼的偵錯工具。 如需偵錯的詳細資訊，請瀏覽[偵錯](./debugging.md)一文。

偵錯工具包含特殊類型的豐富視覺化檢視，例如字串、色彩、Url，以及大小、座標和貝茲曲線。

如需偵錯工具之資料視覺效果的詳細資訊，請瀏覽[資料視覺效果](./data-visualizations.md)一文。

## <a name="version-control"></a>版本控制

Visual Studio for Mac 與 Git 和子版本原始檔控制系統整合。 進行原始檔控制的專案會以解決方案名稱旁邊的分支表示：

![分支名稱指出專案進行原始檔控制](media/ide-tour-image22.png)

具有未認可之變更的檔案，在 [方案] 視窗中的圖示上會有批註，如下圖所示：

![方案視窗中未認可的檔案](media/ide-tour-image23.png)

如需在 Visual Studio 中使用版本控制的詳細資訊，請查看[版本控制](./version-control.md)一文。

## <a name="next-steps"></a>後續步驟

- [安裝 Visual Studio for Mac](installation.md)
- [檢閱可用的工作負載](workloads.md)

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>另請參閱

- [Visual Studio IDE (在 Windows 上)](/visualstudio/ide/visual-studio-ide)