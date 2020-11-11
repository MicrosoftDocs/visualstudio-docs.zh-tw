---
title: 在專案中包含 NuGet 套件
description: 本檔涵蓋如何使用 Visual Studio for Mac 在專案中包含 NuGet 套件。 它會逐步尋找和下載套件，以及介紹 IDE 整合功能。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 46ceb99617c6a0e9ba457fdb769c1162090d1d31
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493487"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中安裝和管理 NuGet 套件

Visual Studio for Mac 中的 NuGet 封裝管理員 UI 可讓您輕鬆地在專案和解決方案中安裝、卸載及更新 NuGet 套件。 您可以搜尋套件，並將其新增至您的 .NET Core、ASP.NET Core 和 Xamarin 專案。

本文描述如何在專案中包含 NuGet 套件，並示範讓處理序順暢處理的工具鏈。

如需在 Visual Studio for Mac 中使用 NuGet 的簡介，請參閱 [快速入門：在 Visual Studio for Mac 中安裝和使用套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>尋找並安裝套件

1. 在 Visual Studio for Mac 中開啟專案時，如果使用 [ **方案] 視窗** 中的 Xamarin 專案) ，請以滑鼠右鍵 **按一下 [相依** 性] 資料夾 ([ **套件** ] 資料夾，然後選取 [ **管理 NuGet 套件 ...** ]。

    ![新增 NuGet 套件內容動作](media/nuget-walkthrough-packages-menu.png)

2. 這會啟動 [ **管理 NuGet 封裝** ] 視窗。 確定對話方塊左上角的 [來源] 下拉式清單設定為 `nuget.org` ，讓您搜尋中央 NuGet 套件存放庫。

    ![列出 NuGet 套件](media/nuget-walkthrough-add-packages1.png)

3. 使用右上角的 [搜尋] 方塊來尋找特定套件，例如 `EntityFramework`。 當您發現想要使用的套件時，請選取該套件，然後按一下 [新增套件] 按鈕開始安裝。

    ![新增 EntityFramework NuGet 套件](media/nuget-walkthrough-add-packages2.png)

4. 套件在下載之後就會新增至您的專案。 解決方案會根據您要編輯的專案類型而變更：

    **Xamarin 專案**
    * [參考] 節點將包含屬於 NuGet 套件一部分的所有組件清單。
    * [套件] 節點會顯示您已下載的每個 NuGet 套件。 您可以更新或移除此清單中的套件。
    
    **.NET Core 專案**

    * [相依性 **>] nuget** 節點會顯示您已下載的每個 nuget 套件。 您可以更新或移除此清單中的套件。

## <a name="using-nuget-packages"></a>使用 NuGet 套件

新增 NuGet 套件並更新專案參考之後，即可針對 API 進行程式設計，如同任何專案參考。

確定您將任何必要 `using` 指示詞新增至檔案頂端：

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>更新套件

封裝更新可以一次完成，方法是以滑鼠右鍵按一下 Xamarin 專案的 [相依性] 節點 ([ **套件** **]** 節點) ，或個別的套件。 當有新版本的 NuGet 套件可用時，更新圖示會顯示 ![ 具有圓形的向上箭號 ](media/nuget-walkthrough-update-icon.png) 。

以滑鼠右鍵按一下相依性以存取內容功能表，並選擇 [ **更新** **]** 以更新所有套件：

![醒目提示 [更新] 功能表的相依性內容功能表](media/nuget-walkthrough-packages-menu-update.png)

* **管理 NuGet 套件** -開啟視窗，將更多套件新增至專案。
* **更新** - 檢查每個套件的來源伺服器，然後下載任何較新版本。
* **還原** - 下載任何遺漏的套件 (不會將現有套件更新為較新版本)。

方案層級也會提供 [更新] 和 [還原] 選項，而且這些選項會影響方案中的所有專案。

### <a name="updating-to-pre-release-versions-of-packages"></a>更新為套件的發行前版本
若要更新為套件的較新發行前版本，您可以在 [相依性] 上按一下滑鼠右鍵以開啟操作功能表，然後選擇 [ **管理 NuGet 套件 ...** **]** 功能表。

![具有管理 NuGet 套件的相依性內容功能表 .。。功能表已反白顯示](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

勾選對話方塊底部的 [ **顯示發行前版本套件** ] 核取方塊。

![已核取 [顯示發行前版本套件] 選項來開啟 [管理 NuGet 套件] 對話方塊](media/nuget-walkthrough-show-pre-release-packages.png)

最後，從對話方塊的 [ **更新** ] 索引標籤中，選取您要更新的套件，並從 [ **新版本** ] 下拉式清單中選擇新的發行前版本，然後按一下 [ **更新套件** ]。

![[管理 NuGet 封裝] 對話方塊開啟至 [已安裝] 索引標籤，並選取套件並開啟新版本下拉式清單。](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>找出過期的封裝
從 [方案] 視窗中，您可以查看目前已安裝的套件版本，然後以滑鼠右鍵按一下要更新的套件。

![具有可更新、移除、重新整理之選項的封裝功能表](media/nuget-walkthrough-PackageMenu.png)

當有新版本的套件可用時，您也會在套件名稱旁邊看到通知，讓您可以決定是否要更新它。

![有新的套件版本可供使用時顯示的通知](media/nuget-walkthrough-package-update-available.png)

在顯示的功能表中，您有兩個選項：

* **更新** - 檢查來源伺服器，然後下載較新版本 (如果已存在)。
* **移除** - 從這個專案中移除套件，並從專案的參考中移除相關組件。

## <a name="manage-packages-for-the-solution"></a>管理解決方案的套件

管理解決方案的套件可讓同時處理多個專案更方便。

1. 以滑鼠右鍵按一下方案，然後選取 [ **管理 NuGet 套件 ...** ：

    ![管理解決方案的 NuGet 套件](media/nuget-walkthrough-manage-packages-solution.png)

1. 在管理解決方案的套件時，UI 可讓您選取受作業影響的專案：

    ![管理解決方案套件時的專案選取器](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>[合併] 索引標籤

在具有多個專案的方案中工作時，最佳作法是確定您在每個專案中使用相同 NuGet 套件的任何位置，也會使用該套件的相同版本號碼。 當您選擇管理解決方案的套件時，Visual Studio for Mac 可在封裝管理員 UI 中提供 [ **合併** ] 索引標籤，以簡化這項作業。 使用此索引標籤，您可以輕鬆地看到解決方案中的不同專案使用具有不同版本號碼的套件：

![套件管理員 UI [合併] 索引標籤](media/nuget-walkthrough-consolidate-tab.png)

在此範例中，NuGetDemo 專案是使用 Microsoft.entityframeworkcore 2.20，而 NuGetDemo 則是使用 Microsoft. Microsoft.entityframeworkcore 2.2.6。 若要合併套件版本，請執行下列動作：

- 在 [專案] 清單中選取要更新的專案。
- 在 **新版本** 清單中選取要在所有這些專案中使用的版本，例如 microsoft.entityframeworkcore 3.0.0。
- 選取 [ **合併套件** ] 按鈕。

套件管理員會將選取的套件版本安裝到所有已選取的專案中，之後套件就不會再出現在 [合併] 索引標籤上。

## <a name="adding-package-sources"></a>新增套件來源

一開始會從 nuget.org 中取出可供安裝的套件。不過，您可以將其他封裝位置新增至 Visual Studio for Mac。 這適用於測試您自己正在開發的 NuGet 套件，或在公司或組織內使用私用 NuGet 伺服器。

在 Visual Studio for Mac 中，巡覽至 [Visual Studio] > [喜好設定] > [NuGet] > [來源] 來檢視和編輯套件來源清單。 請注意，來源可以是遠端伺服器 (由 URL 指定) 或本機目錄。

![套件來源](media/nuget-walkthrough-PackageSource.png)

按一下 [新增] 設定新來源。 輸入套件來源的易記名稱和 URL (或檔案路徑)。 如果來源是安全網頁伺服器，也請輸入使用者名稱和密碼，否則請將這些項目留白：

![[新增套件來源] 對話方塊，其中包含 [名稱]、[位置 URL]、[使用者名稱] 和 [密碼] 提示。](media/nuget-walkthrough-PackageSource2.png)

搜尋套件時，可以選取不同的來源：

![[新增套件來源] 對話方塊，顯示包含套件來源清單的下拉式清單。](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>版本控制

NuGet 文件討論 [using NuGet without committing packages to source control](/nuget/consume-packages/packages-and-source-control) (在未將套件認可到原始檔控制的情況下使用 NuGet)。 如果您不想要將二進位檔和未使用的資訊儲存至原始檔控制，則可以設定 Visual Studio for Mac 自動從伺服器還原套件。 這表示，開發人員第一次從原始檔控制擷取專案時，Visual Studio for Mac 將會自動下載並安裝必要的套件。

![自動還原套件](media/nuget-walkthrough-AutoRestore.png)

如需如何排除 `packages` 目錄不進行追蹤的詳細資料，請參閱特定原始檔控制文件。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>請參閱

* [在 Visual Studio 中安裝並使用套件 (Windows 上)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
