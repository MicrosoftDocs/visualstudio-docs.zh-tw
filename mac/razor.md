---
title: 創建 Razor Web 應用
description: 提供有關 Mac 視覺化工作室中ASP.NET核心應用中 Razor 支援的資訊。
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: fe9ef921ccfc42b77bd08925805aeac6f4aec777
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715884"
---
# <a name="create-razor-web-apps"></a>創建 Razor Web 應用

本指南介紹了創建第一個 Razor Web 應用的介紹。 有關更深入的指導，請參閱 ASP.NET[核心 中的剃刀頁面簡介](/aspnet/core/razor-pages/index)。

Visual Studio for Mac 提供對 Razor 編輯的支援，包含 *.cshtml* 檔案中的 IntelliSense 和語法醒目提示。 Mac 8.3+ 的 Visual Studio 2019 中的新增功能是能夠在 Razor 檔中讓上下文感知 IntelliSense，以便您收到與您當前在文檔中編輯的語言相匹配的 IntelliSense。

![Visual Studio for Mac 中的 Razor 編輯](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>建立新的 Razor 專案

1. 在歡迎畫面上，選擇 **"新建"** 以創建新專案：

   ![Visual Studio for Mac [新增] 對話方塊](media/razor-new.png)
1. 在 **"新專案**"對話方塊中，轉到 **.NET 核心** > **應用** > **Web 應用程式**並選擇 **"下一步**" ：

   ![Razor 專案範本](media/razor-new-project1.png)
1. 選擇 .NET 核心目標框架（我們建議版本 2.2 或更高版本），然後選擇 **"下一步**"。 為專案選擇名稱，並在必要時添加 Git 支援。 選取 [Create] \(建立\)**** 以建立專案。

   ![Razor 專案名稱](media/razor-new-project2.png)

   Mac 視覺化工作室在"代碼"佈局視窗中打開您的專案。
1. 使用**命令_Option_F5**在不調試的情況下運行專案。

   視覺工作室啟動[Kestrel，](/aspnet/core/fundamentals/servers/kestrel)打開瀏覽器到`https://localhost:5001`，並顯示您的第一個 Razor Web 應用程式。

   ![Safari 中的 Razor Web 應用程式](media/razor-webapp.png)

## <a name="project-anatomy"></a>專案解析

Razor Web 應用包括以下元件。

### <a name="pages-folder"></a>Pages 資料夾

此資料夾包含專案的網頁，以及每個網頁的代碼隱藏：
   - HTML 標籤和 Razor 語法的*\*.cshtml*檔。
   - 用於處理頁面事件的 C# 代碼後面的*\*.cshtml.cs*檔。

支援檔案的名稱以底線開頭。 例如，_Layout.cshtml 檔案會設定所有頁面通用的 UI 元素。 此檔設置頁面頂部的導航功能表和底部的版權聲明。 如需詳細資訊，請參 [ASP.NET 中的配置](/aspnet/core/mvc/views/layout)。

### <a name="launch-settings"></a>啟動設定

*啟動設置.json*檔包含 IIS 設置、應用程式 URL 和其他相關設置。

### <a name="app-settings"></a>應用程式設定

*appSettings.json*檔包含配置資料，如連接字串。

有關配置的詳細資訊，請參閱 ASP.NET[指南中的配置](/aspnet/core/fundamentals/configuration/index)。

### <a name="wwwroot-folder"></a>wwwroot 資料夾

此資料夾包含靜態檔，如 HTML、JavaScript 和 CSS 檔。 如需詳細資訊，請參閱 [ASP.NET Core 中的靜態檔案](/aspnet/core/fundamentals/static-files)。

### <a name="programcs"></a>Program.cs

此檔包含程式的進入點。 如需詳細資訊，請參閱 [ASP.NET Core Web 主機](/aspnet/core/fundamentals/host/web-host)。

### <a name="startupcs"></a>Startup.cs

此檔包含配置應用行為的代碼，例如應用是否需要 Cookie 的同意。 如需詳細資訊，請參閱 [ASP.NET Core 中的應用程式啟動](/aspnet/core/fundamentals/startup)。

## <a name="see-also"></a>另請參閱

有關創建 Razor Web 應用的更全面的指南，請參閱[ASP.NET 酷睿版中的 Razor 頁面簡介](/aspnet/core/razor-pages/index)。
