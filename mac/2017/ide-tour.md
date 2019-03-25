---
title: Visual Studio for Mac 教學課程
description: Visual Studio for Mac 提供整合式的開發環境，以在 macOS 上建置 .NET 應用程式，包括 ASP.NET Core 網站，和適用於 iOS、Android、Mac 和 Xamarin.Forms 的 Xamarin 專案。
author: conceptdev
ms.author: crdun
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 238370c5f8de5efdb37a29fea9d3e91763a0aa18
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58070031"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Visual Studio 2017 for Mac 導覽

> [!NOTE]
> Visual Studio 2019 for Mac [現已開放](installation.md?view=vsmac-2019)以預覽版形式進行測試。

Visual Studio for Mac 是 Mac 上的 _.NET 整合式開發環境_，可用來編輯、偵錯及建置程式碼，然後發佈應用程式。 除了必備功能 (如標準編輯器和偵錯工具) 外，Visual Studio for Mac 還有編譯器、程式碼完成工具、圖形設計工具和原始檔控制，讓軟體開發程序變得輕鬆容易。

Visual Studio for Mac 支援的檔案類型很多都與 Windows 相同，例如 `.csproj`、`.fsproj`或 `.sln` 檔案，也支援 EditorConfig 這類功能，也就是說，您可以使用最適合您的 IDE。
建立、開啟及開發應用程式，對於先前在 Windows 上使用 Visual Studio 的任何人而言，將會是熟悉的經驗。 此外，Visual Studio for Mac 採用許多功能強大的工具，這些工具讓其 Windows 對等項目成為功能如此強大的 IDE。 Roslyn 編譯器平台用於重構和 IntelliSense。 其專案系統和組建引擎會使用 MSBuild，而其原始檔編輯器則支援 TextMate 組合。 它為 Xamarin 與 .NET Core 應用程式使用相同的偵錯工具引擎，並為 Xamarin.iOS 和 Xamarin.Android 使用相同的設計工具。

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Visual Studio for Mac 內含哪些功能

Visual Studio for Mac 支援下列幾種開發作業：

- 使用 C#、F# 開發 ASP.NET Core web 應用程式，並支援 Razor Pages、JavaScript 和 TypeScript
- 使用 C# 或 F# 開發 .NET Core 主控台應用程式
- 使用 C# 開發跨平台 Unity 遊戲和應用程式
- 使用 C# 或 F# 和 XAML 在 Xamarin 中開發 Android、iOS、tvOS 和 watchOS 應用程式
- 使用 C# 或 F# 開發 Cocoa 傳統型應用程式

此文章探討 Visual Studio for Mac 的各個部分，提供一些功能的相關資訊，讓它成為建立這些應用程式的強大工具。

## <a name="ide-tour"></a>IDE 教學課程

Visual Studio for Mac 分成數個區段，以便管理應用程式檔案和設定、建立應用程式程式碼及偵錯。

## <a name="welcome-screen"></a>歡迎畫面

啟動時，Visual Studio for Mac 會顯示*歡迎畫面*：

![歡迎畫面](media/ide-tour-image1.png)

歡迎畫面包含下列區段：

- **工具列** - 提供搜尋列的快速存取。 載入方案時，工具列會用來設定應用程式設定、進行偵錯，以及顯示錯誤。
- **使用者入門** - 為開始使用 Visual Studio for Mac 的開發人員提供實用主題的快速存取。
- **最近使用的解決方案** - 提供最近開啟之解決方案的快速存取，以及開啟或建立專案的便利按鈕。
- **開發人員新聞** - 可讓您掌握最新 Microsoft 開發人員資訊的新聞摘要。

## <a name="solutions-and-projects"></a>專案和方案

下圖顯示已載入應用程式的 Visual Studio for Mac：

![已載入應用程式的 Visual Studio for Mac](media/ide-tour-image17.png)

下列各節提供 Visual Studio for Mac 中主要區域的概觀。

## <a name="solution-pad"></a>Solution Pad

Solution Pad 能組織方案中的專案：

![專案組織在 Solution Pad 中](media/ide-tour-image18.png)

這是原始碼、資源、使用者介面和相依性的檔案組織成平台專屬專案的位置。

如需在 Visual Studio for Mac 中使用專案和方案的詳細資訊，請參閱[專案和方案](/visualstudio/mac/projects-and-solutions)一文。

## <a name="assembly-references"></a>組件參考

每個專案的組件參考，提供於 [參考] 資料夾底下：

![Solution Pad 中的 [參考] 資料夾](media/ide-tour-image19.png)

其他參考資料是使用 [編輯參考] 對話方塊來新增，其顯示方法是在 [參考] 資料夾上按兩下，或在其操作功能表動作上選取 [編輯參考]：

![[編輯參考] 對話方塊](media/ide-tour-image20.png)

如需在 Visual Studio for Mac 中使用參考的詳細資訊，請參閱[管理專案中的參考](/visualstudio/mac/managing-references-in-a-project)一文。

## <a name="dependencies--packages"></a>相依性/套件

用於應用程式中的所有外部相依性，都會儲存在 [相依性] 或 [套件] 資料夾中，視您是在 .Net Core 或 Xamarin.iOS/Xamarin.Android 專案中而定。 這些通常會以 NuGet 的形式提供。

NuGet 是適用於 .NET 開發最受歡迎的套件管理員。 使用 Visual Studio 的 NuGet 支援，您可以輕鬆地搜尋並新增套件至您的應用程式專案。

若要將相依性新增至應用程式，請以滑鼠右鍵按一下 [相依性] / [套件] 資料夾，然後選取 [新增套件]：

![新增 NuGet 套件](media/ide-tour-image21.png)

在應用程式中使用 NuGet 套件的相關資訊，可於[在專案中包含 NuGet 專案](/visualstudio/mac/nuget-walkthrough)一文中找到。

## <a name="refactoring"></a>重構

Visual Studio for Mac 提供兩種有用的方式來重構程式碼：內容動作和來源分析。 您可以在[重構](/visualstudio/mac/refactoring)一文中閱讀有關它們的深入資訊。

## <a name="debugging"></a>偵錯

Visual Studio for Mac 具有原生偵錯工具，能夠支援 Xamarin.iOS、 Xamarin.Mac 和 Xamarin.Android 應用程式的偵錯。 Visual Studio for Mac 使用 Mono Soft Debugger，它實作到 Mono 執行階段之中，讓 IDE 能跨所有平台進行 Managed 程式碼的偵錯。 如需偵錯的詳細資訊，請瀏覽[偵錯](/visualstudio/mac/debugging)一文。

偵錯工具包含豐富的視覺化檢視，適用於特殊類型，例如字串、色彩、URL、大小、座標，以及貝茲曲線。

如需偵錯工具之資料視覺效果的詳細資訊，請瀏覽[資料視覺效果](/visualstudio/mac/data-visualizations)一文。

## <a name="version-control"></a>版本控制

Visual Studio for Mac 與 Git 和子版本原始檔控制系統整合。 進行原始檔控制的專案會以解決方案名稱旁邊的分支表示：

![分支名稱指出專案進行原始檔控制](media/ide-tour-image22.png)

具有未認可之變更的檔案，在 [方案窗格] 中的圖示上會有註釋，如下圖所示：

![Solution Pad 中的未認可檔案](media/ide-tour-image23.png)

如需在 Visual Studio 中使用版本控制的詳細資訊，請查看[版本控制](/visualstudio/mac/version-control)一文。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]


## <a name="see-also"></a>另請參閱

- [Visual Studio IDE (Windows 上)](/visualstudio/ide/visual-studio-ide)
