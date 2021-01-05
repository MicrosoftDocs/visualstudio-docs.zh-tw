---
title: 在專案中包含 NuGet 套件
description: 本文件涵蓋如何在 Xamarin 專案中包含 NuGet 套件。 它會逐步尋找和下載套件，以及介紹 IDE 整合功能。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 274e8defe25fa78c30aee72834e486b302a9af4e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729427"
---
# <a name="include-a-nuget-package-in-your-project"></a>在專案中包含 NuGet 套件

NuGet 是進行 .NET 開發的最受歡迎套件管理員，並內建於 Visual Studio for Mac 以及 Windows 上的 Visual Studio。 您可以使用任一 IDE 來搜尋套件，並將其新增至 Xamarin.iOS 和 Xamarin.Android 專案。

本文描述如何在專案中包含 NuGet 套件，並示範讓處理序順暢處理的工具鏈。

## <a name="nuget-in-visual-studio-for-mac"></a>Visual Studio for Mac 中的 NuGet

為了示範 NuGet 套件功能，我們會先逐步建立新的應用程式，並在其中新增套件。 接著，我們將討論可協助管理套件的 IDE 功能。

## <a name="create-a-new-project"></a>建立新專案

首先，建立名為 `HelloNuget` 的專案，如下所示。 此範例顯示「iOS 單一檢視應用程式」範本，但會使用任何支援的專案類型：

![建立新 iOS 專案](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>新增套件

在 Visual Studio for Mac 中開啟專案時，以滑鼠右鍵按一下 [Solution Pad] 中的 [套件] 資料夾，然後選取 [新增套件]：

![新增 NuGet 套件內容動作](media/nuget-walkthrough-PackagesMenu.png)

這會啟動 [新增套件] 視窗。 確定 [來源] 下拉式清單設定為 `nuget.org`：

![來源清單下拉式清單](media/nuget-walkthrough-Source.png)

當視窗開啟時，會從預設套件來源載入套件清單： nuget.org。初始結果看起來像這樣：

![列出 NuGet 套件](media/nuget-walkthrough-AddPackages1.png)

使用右上角的 [搜尋] 方塊來尋找特定套件，例如 `azure`。 當您發現想要使用的套件時，請選取它，然後按一下 [新增套件] 按鈕開始安裝。

[新增 Azure NuGet 套件](media/nuget-walkthrough-AddPackages2.png)

套件在下載之後就會新增至您的專案。 會如下變更方案：

* [參考] 節點將包含屬於 NuGet 套件一部分的所有組件清單。
* [套件] 節點會顯示您已下載的每個 NuGet 套件。 您可以更新或移除此清單中的套件。
* **packages.config** 檔案將會新增至專案。 IDE 使用此 XML 檔案來追蹤這個專案中所參考的套件版本。 這個檔案不應該手動進行編輯，但您應該將它保留在版本控制中。 請注意，可以使用 project.json 檔案，而不要使用 packages.config 檔案。 project.json 檔案是支援可轉移還原之 NuGet 3 引進的新套件檔案格式。 如需 project.json 的詳細資訊，請參閱 [NuGet 文件](/NuGet/Schema/Project-Json)。 需要手動新增 project.json 檔案，以及先關閉並重新開啟專案，再將 project.json 檔案用於 Visual Studio for Mac 中。

## <a name="using-nuget-packages"></a>使用 NuGet 套件

新增 NuGet 套件並更新專案參考之後，即可針對 API 進行程式設計，如同任何專案參考。

確定您將任何必要 `using` 指示詞新增至檔案頂端：

```csharp
using Newtonsoft.Json;
```

大部分 NuGet 都會提供其他資訊，例如 Nuget 來源的 README 或專案頁面連結。 您通常可以在 [新增套件] 頁面的套件簡介上找到此項目的連結：

[檢視專案頁面連結](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>套件更新

以滑鼠右鍵按一下 [套件] 節點，或分別以滑鼠右鍵按一下每個元件，即可一次完成所有套件更新。

以滑鼠右鍵按一下 [套件] 來存取操作功能表：

![螢幕擷取畫面，顯示已選取 [套件] 節點，並以命令開啟以新增套件、更新、還原和重新整理的滑鼠右鍵內容功能表。](media/nuget-walkthrough-PackagesMenu.png)

* **新增套件** - 開啟視窗，將更多套件新增至專案。
* **更新** - 檢查每個套件的來源伺服器，然後下載任何較新版本。
* **還原** - 下載任何遺漏的套件 (不會將現有套件更新為較新版本)。

方案層級也會提供 [更新] 和 [還原] 選項，而且這些選項會影響方案中的所有專案。

您也可以以滑鼠右鍵按一下個別套件，來存取操作功能表：

![顯示已選取個別套件的螢幕擷取畫面，並開啟具有更新、移除和重新整理命令的滑鼠右鍵內容功能表。](media/nuget-walkthrough-PackageMenu.png)

* **版本號碼** - 版本號碼是停用的功能表項目；這僅供參考。
* **更新** - 檢查來源伺服器，然後下載較新版本 (如果已存在)。
* **移除** - 從這個專案中移除套件，並從專案的參考中移除相關組件。

## <a name="adding-package-sources"></a>新增套件來源

一開始會從 nuget.org 中取出可供安裝的套件。不過，您可以將其他封裝位置新增至 Visual Studio for Mac。 這適用於測試您自己正在開發的 NuGet 套件，或在公司或組織內使用私用 NuGet 伺服器。

在 Visual Studio for Mac 中，巡覽至 [Visual Studio] > [喜好設定] > [NuGet] > [來源] 來檢視和編輯套件來源清單。 請注意，來源可以是遠端伺服器 (由 URL 指定) 或本機目錄。

![套件來源](media/nuget-walkthrough-PackageSource.png)

按一下 [新增] 設定新來源。 輸入套件來源的易記名稱和 URL (或檔案路徑)。 如果來源是安全網頁伺服器，也請輸入使用者名稱和密碼，否則請將這些項目留白：

![[新增套件來源] 對話方塊的螢幕擷取畫面，其中包含名稱、位置、使用者名稱和密碼的欄位。](media/nuget-walkthrough-PackageSource2.png)

搜尋套件時，可以選取不同的來源：

![[新增套件] 畫面的螢幕擷取畫面，其中顯示搜尋套件時可選取的來源下拉式清單。](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>版本控制

NuGet 文件討論 [using NuGet without committing packages to source control](/nuget/consume-packages/packages-and-source-control) (在未將套件認可到原始檔控制的情況下使用 NuGet)。 如果您不想要將二進位檔和未使用的資訊儲存至原始檔控制，則可以設定 Visual Studio for Mac 自動從伺服器還原套件。 這表示，開發人員第一次從原始檔控制擷取專案時，Visual Studio for Mac 將會自動下載並安裝必要的套件。

![自動還原套件](media/nuget-walkthrough-AutoRestore.png)

如需如何排除 `packages` 目錄不進行追蹤的詳細資料，請參閱特定原始檔控制文件。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>請參閱

* [在 Visual Studio 中安裝並使用套件 (Windows 上)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
