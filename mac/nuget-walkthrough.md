---
title: 在專案中包含 NuGet 套件
description: 本文檔介紹如何在使用 Mac 視覺化工作室的專案中包括 NuGet 包。 它會逐步尋找和下載套件，以及介紹 IDE 整合功能。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127221"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>在 Mac 視覺化工作室中安裝和管理 NuGet 套裝軟體

適用于 Mac 的 Visual Studio 中的 NuGet 包管理器 UI 允許您輕鬆地在專案和解決方案中安裝、卸載和更新 NuGet 包。 您可以搜索 .NET Core、ASP.NET核心和 Xamarin 專案中的包並將其添加到專案中。

本文描述如何在專案中包含 NuGet 套件，並示範讓處理序順暢處理的工具鏈。

有關在 Mac 視覺化工作室中使用 NuGet 的介紹，請參閱[快速入門：在 Mac 視覺化工作室中安裝和使用包](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>查找並安裝包

1. 在 Mac 的 Visual Studio 中打開專案後，按右鍵**解決方案墊**中的 **"依賴項**"資料夾（如果使用 Xamarin 專案，**則使用"包**"資料夾），然後選擇"**管理 NuGet 包..."。**

    ![新增 NuGet 套件內容動作](media/nuget-walkthrough-packages-menu.png)

2. 這將啟動 **"管理 NuGet 包"** 視窗。 確保對話方塊左上角的源下拉設置為`nuget.org`，以便搜索中央 NuGet 包存儲庫。

    ![列出 NuGet 套件](media/nuget-walkthrough-add-packages1.png)

3. 使用右上角的 [搜尋] 方塊來尋找特定套件，例如 `EntityFramework`。 當您發現想要使用的套件時，請選取該套件，然後按一下 [新增套件]**** 按鈕開始安裝。

    ![添加實體框架 NuGet 包](media/nuget-walkthrough-add-packages2.png)

4. 套件在下載之後就會新增至您的專案。 解決方案將根據您編輯的專案類型而變化：

    **夏馬林專案**
    * [參考]**** 節點將包含屬於 NuGet 套件一部分的所有組件清單。
    * [套件]**** 節點會顯示您已下載的每個 NuGet 套件。 您可以更新或移除此清單中的套件。
    
    **.NET 核心專案**

    * **NuGet 節點>依賴項**顯示已下載的每個 NuGet 包。 您可以更新或移除此清單中的套件。

## <a name="using-nuget-packages"></a>使用 NuGet 套件

新增 NuGet 套件並更新專案參考之後，即可針對 API 進行程式設計，如同任何專案參考。

確定您將任何必要 `using` 指示詞新增至檔案頂端：

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>更新包

包更新可以一次完成，通過按右鍵**依賴項**節點（Xamarin 專案的**包**節點），也可以在每個包上單獨按一下。 當新版本的 NuGet 包可用時，更新圖示將顯示![一個帶圓圈](media/nuget-walkthrough-update-icon.png)的向上箭號。

按右鍵**依賴項**以訪問內容功能表，然後選擇 **"更新**"以更新所有包：

![套件功能表](media/nuget-walkthrough-packages-menu-update.png)

* **管理 NuGet 包**- 打開視窗以向專案添加更多包。
* **更新** - 檢查每個套件的來源伺服器，然後下載任何較新版本。
* **還原** - 下載任何遺漏的套件 (不會將現有套件更新為較新版本)。

方案層級也會提供 [更新] 和 [還原] 選項，而且這些選項會影響方案中的所有專案。

### <a name="locating-outdated-packages"></a>查找過期包
在解決方案墊中，您可以查看當前安裝的包版本，並按右鍵要更新的包。

![包含更新、刪除、刷新選項的包式功能表](media/nuget-walkthrough-PackageMenu.png)

當包的新版本可用時，您還會在包名稱旁邊看到一條通知，以便您可以決定是否要更新它。

![新包版本可用時顯示的通知](media/nuget-walkthrough-package-update-available.png)

在顯示的功能表中，您有兩個選項：

* **更新** - 檢查來源伺服器，然後下載較新版本 (如果已存在)。
* **移除** - 從這個專案中移除套件，並從專案的參考中移除相關組件。

## <a name="manage-packages-for-the-solution"></a>管理解決方案的套件

管理解決方案的套件可讓同時處理多個專案更方便。

1. 按右鍵解決方案並選擇 **"管理 NuGet 包..."：**

    ![管理解決方案的 NuGet 套件](media/nuget-walkthrough-manage-packages-solution.png)

1. 在管理解決方案的套件時，UI 可讓您選取受作業影響的專案：

    ![管理解決方案套件時的專案選取器](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>[合併] 索引標籤

在具有多個專案的解決方案中工作時，最佳做法是確保在每個專案中使用相同的 NuGet 包的任意位置，您也使用相同的包版本號。 當您選擇管理解決方案的包時，Mac 的 Visual Studio 通過在"打包管理器"UI 中提供 **"合併**"選項卡，有助於簡化此功能。 使用此選項卡，您可以輕鬆地查看解決方案中不同專案使用不同版本號的包的位置：

![套件管理員 UI [合併] 索引標籤](media/nuget-walkthrough-consolidate-tab.png)

在此示例中，NuGetDemo 專案使用 Microsoft.EntityFrameworkCore 2.20，而 NuGetDemo.Shared 使用 Microsoft.EntityFrameworkCore 2.2.6。 若要合併套件版本，請執行下列動作：

- 在 [專案] 清單中選取要更新的專案。
- 選擇要在**新版本**清單中的所有這些專案中使用的版本，例如 Microsoft.EntityFrameworkCore 3.0.0.0。
- 選擇"**合併包**"按鈕。

套件管理員會將選取的套件版本安裝到所有已選取的專案中，之後套件就不會再出現在 [合併]**** 索引標籤上。

## <a name="adding-package-sources"></a>新增套件來源

最初可從nuget.org檢索可用於安裝的包。但是，您可以將其他包位置添加到 Mac 的 Visual Studio。 這適用於測試您自己正在開發的 NuGet 套件，或在公司或組織內使用私用 NuGet 伺服器。

在 Visual Studio for Mac 中，巡覽至 [Visual Studio] > [喜好設定] > [NuGet] > [來源]**** 來檢視和編輯套件來源清單。 請注意，來源可以是遠端伺服器 (由 URL 指定) 或本機目錄。

![套件來源](media/nuget-walkthrough-PackageSource.png)

按一下 [新增]**** 設定新來源。 輸入套件來源的易記名稱和 URL (或檔案路徑)。 如果來源是安全網頁伺服器，也請輸入使用者名稱和密碼，否則請將這些項目留白：

![新增套件來源](media/nuget-walkthrough-PackageSource2.png)

搜尋套件時，可以選取不同的來源：

![新增套件來源](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>版本控制

NuGet 文件討論 [using NuGet without committing packages to source control](/nuget/consume-packages/packages-and-source-control) (在未將套件認可到原始檔控制的情況下使用 NuGet)。 如果您不想要將二進位檔和未使用的資訊儲存至原始檔控制，則可以設定 Visual Studio for Mac 自動從伺服器還原套件。 這表示，開發人員第一次從原始檔控制擷取專案時，Visual Studio for Mac 將會自動下載並安裝必要的套件。

![自動還原套件](media/nuget-walkthrough-AutoRestore.png)

如需如何排除 `packages` 目錄不進行追蹤的詳細資料，請參閱特定原始檔控制文件。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>另請參閱

* [在 Visual Studio 中安裝並使用套件 (Windows 上)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
