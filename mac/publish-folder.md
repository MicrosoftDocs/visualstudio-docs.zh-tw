---
title: 發行至資料夾
description: 如何使用 Visual Studio for Mac 將 web 應用程式發行至資料夾。
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 99127416b6a488cd7e795b3c4a1888ff103c8029
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607388"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>使用 Visual Studio for Mac 發行至資料夾

您可以使用發行工具，將 .NET Core 主控台或 ASP.NET Core 應用程式發佈到資料夾。

## <a name="prerequisites"></a>必要條件

- 安裝了 .NET Core 的[Visual Studio 2019 For Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) 。
- .NET Core 主控台或 ASP.NET Core 專案。 如果您還沒有專案，可以[建立新的專案](./create-new-projects.md)。

## <a name="publish-to-folder"></a>發佈到資料夾

使用 Visual Studio for Mac，您可以使用 [發行] 工具，將您的 .NET Core 專案發行到資料夾。 發行到資料夾之後，您可以將檔案傳送到不同的環境。 若要發佈到資料夾，請執行下列步驟。

 1. 在 [方案] 視窗中，以滑鼠右鍵按一下專案，然後選擇 [ **發行**]。

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

若要變更發行設定檔的名稱 (這會顯示在 [發佈] 操作功能表中)，請重新命名發行設定檔。 請勿變更檔案的副檔名 (`.pubxml`)。

若要變更發佈資料夾路徑，請開啟發行設定檔並編輯 `publishUrl` 值。

若要變更使用的組建組態，請變更發行設定檔中的 `LastUsedBuildConfiguration` 屬性。

## <a name="see-also"></a>另請參閱
 - [dotnet publish](https://docs.microsoft.com/dotnet/core/tools/dotnet-publish)
 - [使用 Visual Studio 將 Web 應用程式發行至網站 ](https://docs.microsoft.com/visualstudio/deployment/quickstart-deploy-to-a-web-site?view=vs-2019)