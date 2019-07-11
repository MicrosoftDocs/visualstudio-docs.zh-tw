---
title: Razor
description: Visual Studio for Mac 中 ASP.NET Core 應用程式的 Razor 支援資訊
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 9e5a3f61ee7065a0615a381bdcc03dafc3566893
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691262"
---
# <a name="razor"></a>Razor

Visual Studio for Mac 提供對 Razor 編輯的支援，包含 *.cshtml* 檔案中的 IntelliSense 和語法醒目提示。

![Visual Studio for Mac 中的 Razor 編輯](media/razor-editor.png)

此指南提供有關建立您的第一個 Razor Web 應用程式的簡介。 如需有關深入指南，請參閱 [.NET Core 中的 Razor Pages 文件](/aspnet/core/razor-pages/index)。

## <a name="creating-a-new-razor-project"></a>建立新的 Razor 專案

* 從歡迎畫面，選取 [新增]  以建立新專案：

![Visual Studio for Mac [新增] 對話方塊](media/razor-new.png)

* 在 [新增專案] 對話方塊中，瀏覽到 [.NET Core]   > [應用程式]   > [Web 應用程式]  並選取 [下一步]  按鈕：

![Razor 專案範本](media/razor-new-project1.png)

* 選取您需要的 .NET Core 目標 Framework (建議使用 2.2 或更新版本) 並選取 [下一步]**Next**。  為您的專案選擇名稱，並視需要新增 git 支援。 選取 [Create] \(建立\)  以建立專案。

![Razor 專案名稱](media/razor-new-project2.png)

Visual Studio for Mac 將會以 [程式碼] 配置開啟您的專案。

* 使用 **Cmd-Opt-F5** 在不執行偵錯的情況下執行專案

Visual Studio 將會啟動 [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) 並啟動連線 `https://localhost:5001` 的瀏覽器，然後顯示您的第一個 Razor Web 應用程式：

![Safari 中的 Razor Web 應用程式](media/razor-webapp.png)

## <a name="project-anatomy"></a>專案解析

Razor Web 應用程式是由下列元件組成的：

### <a name="pages-folder"></a>Pages 資料夾

您可以在專案中的 [Pages] 資料夾中找到網頁，以及每個項目的程式碼後置：
* 用於 HTML 標記與 Razor 語法的 * *.cshtml* 檔案。
* 用於您 C# 程式碼後置的 *.cshtml.cs* 檔案 (用於處以頁面事件)。

支援檔案的名稱以底線開頭。 例如，_Layout.cshtml 檔案會設定所有頁面通用的 UI 元素。 此檔案會設定頁面頂端的導覽功能表和頁面底部的著作權標示。 如需詳細資訊，請參 [ASP.NET 中的配置](https://docs.microsoft.com/aspnet/core/mvc/views/layout)。

### <a name="launch-settings"></a>啟動設定

檔案的 *launchSettings.json* 包含 IIS 設定、應用程式 URL 與其他相關設定。

### <a name="app-settings"></a>應用程式設定

*appSettings,json* 檔案包含設定資料，例如連接字串。

如需有關設定的詳細資訊，請參閱 [ASP.NET Core 中的設定指南](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index)。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

包含靜態檔案，例如 HTML 檔案、JavaScript 檔案和 CSS 檔案。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](https://docs.microsoft.com/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host)。

### <a name="startupcs"></a>Startup.cs

包含設定應用程式行為的程式碼，例如是否需要同意使用 Cookie。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](https://docs.microsoft.com/aspnet/core/fundamentals/startup)。

## <a name="see-aso"></a>另請參閱

如需有關建立 Razor Web 應用程式的完整指南，請參閱 [ASP.NET Core 中的 Razor Pages 簡介](https://docs.microsoft.com/aspnet/core/razor-pages/index)。
