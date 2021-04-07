---
title: 發行至資料夾
description: 您可以使用 [發佈] 工具，將 ASP.NET Core 應用程式發佈到資料夾。
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: e2d1b0bb67c30daf13503196546f3280ceb7a635
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083551"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 將 Web 應用程式發佈到資料夾

您可以使用 [發佈] 工具，將 ASP.NET Core 應用程式發佈到資料夾。

## <a name="prerequisites"></a>必要條件

- 已安裝 [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) 並啟用 ASP.NET Core。
- ASP.NET Core 專案。 如果您還沒有專案，可以[建立新的專案](./create-new-projects.md?view=vsmac-2017&preserve-view=true)。

## <a name="publish-to-folder"></a>發佈到資料夾

使用 Visual Studio for Mac 時，您可以透過 [發佈] 工具將 ASP.NET Core 專案發佈到資料夾。 發佈到資料夾之後，您就可以將檔案傳輸到網頁伺服器，以便匯入不同的環境。 若要發佈到資料夾，請執行下列步驟。

 1. 在 Solution Pad 中，以滑鼠右鍵按一下專案，然後選擇 [發佈]。

    ![[發佈] 操作功能表](media/publish-context-menu.png)

 2. 如果您之前已發佈此專案，您將會在功能表中看到發行設定檔。 選取該發行設定檔即可啟動發佈程序。

 3. 若是第一次將此專案發佈到資料夾，請選取 [發佈到資料夾]

    ![[發佈到資料夾] 操作功能表](media/publish-to-folder-context-menu.png)

 4. [發佈到資料夾] 對話方塊會隨即出現。 在此對話方塊中，您可以自訂要發佈專案的資料夾。 您可以使用 [瀏覽] 按鈕來執行這項作業，或貼至路徑。

 5. 按一下 [發佈] 之後，會發生幾件事。 首先會建立發行設定檔。 發行設定檔是發佈程序期間匯入專案的 MSBuild 檔。 其中包含發佈程序期間所使用的屬性。 這些檔案會儲存在 `Properties/PublishProfiles` 中並具有副檔名 `.pubxml`。 接著會啟動發佈程序。 您可以在 Visual Studio for Mac 中監看狀態列來監視進度。

    ![具有發佈狀態的 IDE 狀態列](media/publish-to-folder-status-bar.png)

 6. 一旦發佈成功完成，[搜尋工具] 視窗就會開啟至發佈資料夾。 現在已建立發行設定檔，它會顯示在 [發佈] 操作功能表中。

    ![具有資料夾設定檔的 [發佈] 操作功能表](media/publish-context-menu-with-folder-profile.png)

 7. 若要使用相同的設定再次發佈專案，您可以按一下 [發佈] 操作功能表中的設定檔。

## <a name="customize-publish-options"></a>自訂發佈選項

若要變更發行設定檔的名稱 (這會顯示在 [發佈] 操作功能表中)，請重新命名發行設定檔。 請勿變更檔案的副檔名 (`.puxbml`)。

若要變更發佈資料夾路徑，請開啟發行設定檔並編輯 `publishUrl` 值。

若要變更使用的組建組態，請變更發行設定檔中的 `LastUsedBuildConfiguration` 屬性。