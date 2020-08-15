---
title: 建立 Razor web 應用程式
description: 提供 Visual Studio for Mac 中 ASP.NET Core 應用程式的 Razor 支援相關資訊。
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 26575367d7aff2b92c64dc5d07068b4900b24e7f
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249542"
---
# <a name="create-razor-web-apps"></a>建立 Razor web 應用程式

本指南提供建立您的第一個 Razor web 應用程式的簡介。 如需更深入的指引，請參閱 [ASP.NET Core 中的 Razor Pages 簡介](/aspnet/core/razor-pages/index)。

Visual Studio for Mac 提供對 Razor 編輯的支援，包含 *.cshtml* 檔案中的 IntelliSense 和語法醒目提示。 Mac 8.3 + Visual Studio 2019 的新功能是在 Razor 檔案中具有內容感知 IntelliSense 的能力，因此您會收到符合您目前在檔中編輯之語言的 IntelliSense。

![Visual Studio for Mac 中的 Razor 編輯](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>建立新的 Razor 專案

1. 在 [歡迎使用] 畫面上，選取 [ **新增** ] 以建立新的專案：

   ![Visual Studio for Mac [新增] 對話方塊](media/razor-new.png)
1. 在 [**新增專案**] 對話方塊中，移至 [ **.net Core**  >  **應用**  >  **程式 Web 應用程式**] 並選取 **[下一步]**：

   ![Razor 專案範本](media/razor-new-project1.png)
1. 選取您的 .NET Core 目標 framework (建議) 2.2 版或更新版本，然後選取 **[下一步]**。 選擇專案的名稱，並在必要時新增 Git 支援。 選取 [Create] \(建立\) 以建立專案。

   ![Razor 專案名稱](media/razor-new-project2.png)

   Visual Studio for Mac 會在 [程式碼配置] 視窗中開啟您的專案。
1. 使用 **Command + Option + F5**執行專案，而不進行任何偵錯工具。

   Visual Studio 啟動 [Kestrel](/aspnet/core/fundamentals/servers/kestrel)，將瀏覽器開啟至 `https://localhost:5001` ，並顯示您的第一個 Razor web 應用程式。

   ![Safari 中的 Razor Web 應用程式](media/razor-webapp.png)

## <a name="project-anatomy"></a>專案剖析

Razor web 應用程式包含下列元件。

### <a name="pages-folder"></a>Pages 資料夾

此資料夾包含專案的網頁，以及每個的程式碼後置：
- HTML 標籤和 Razor 語法的* \* cshtml*檔案。
- 適用于 c # 程式碼後置以處理頁面事件的* \* cshtml.cs*檔案。

支援檔案的名稱以底線開頭。 例如，配置* \_ cshtml*檔案會設定所有頁面通用的 UI 元素。 此檔案會設定頁面頂端的導覽功能表和底部的著作權注意事項。 如需詳細資訊，請參 [ASP.NET 中的配置](/aspnet/core/mvc/views/layout)。

### <a name="launch-settings"></a>啟動設定

檔案 * 上的launchSettings.js* 包含 IIS 設定、應用程式 URL 和其他相關設定。

### <a name="app-settings"></a>應用程式設定

檔案 * 上的appSettings.js* 包含設定資料，例如連接字串。

如需設定的詳細資訊，請參閱 [ASP.NET 中](/aspnet/core/fundamentals/configuration/index)的設定指南。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

此資料夾包含靜態檔案，例如 HTML、JavaScript 和 CSS 檔案。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

此檔案包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)。

### <a name="startupcs"></a>Startup.cs

此檔案包含設定應用程式行為的程式碼，例如應用程式是否需要同意 cookie。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](/aspnet/core/fundamentals/startup)。

## <a name="see-also"></a>另請參閱

如需建立 Razor web 應用程式的更完整指南，請參閱 [ASP.NET Core 中的 Razor Pages 簡介](/aspnet/core/razor-pages/index)。
