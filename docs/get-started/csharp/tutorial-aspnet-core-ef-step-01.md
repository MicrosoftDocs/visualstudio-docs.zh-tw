---
title: 搭配 Entity Framework 與 Visual Studio 2019 的 ASP.NET Core Web 應用程式
titleSuffix: ''
description: 作為建立 ASP.NET Core Web 應用程式前的第一步，請先透過此影片教學課程和逐步指示，了解如何安裝 Visual Studio 2019。
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c6cf4429607f8ceb2a3ed4a5a1cb91274a201698
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922796"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>教學課程：使用 Entity Framework 搭配 Visual Studio 2019 來建立您的第一個 ASP.NET Core 應用程式

在本教學課程中，您將建立可使用資料的 ASP.NET Core Web 應用程式，並將它部署至 Azure。 本教學課程包含下列步驟：

- [步驟1：安裝 Visual Studio 2019](#step-1-install-visual-studio-2019)
- [步驟2：建立您的第一個 ASP.NET Core web 應用程式](tutorial-aspnet-core-ef-step-02.md)
- [步驟3：使用 Entity Framework 處理資料](tutorial-aspnet-core-ef-step-03.md)
- [步驟4：從您的 ASP.NET Core 應用程式公開 web API](tutorial-aspnet-core-ef-step-04.md)
- [步驟5：將您的 ASP.NET Core 應用程式部署至 Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>步驟1：安裝 Visual Studio 2019

透過此影片教學課程和逐步指示，了解如何安裝 Visual Studio 2019。 如果您已經安裝 Visual Studio，請直接跳到 [步驟2：建立您的第一個 ASP.NET Core web 應用程式](tutorial-aspnet-core-ef-step-02.md)。

_觀看此影片並跟著操作，以安裝 Visual Studio 並建立您的第一個 ASP.NET Core 應用程式。_

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>下載安裝程式

移至 [visualstudio.com](https://visualstudio.com) 尋找安裝程式。 找出 Visual Studio 2019 連結，然後按一下以開始下載。 如需 Visual Studio 的免費版本，請選擇 Visual Studio Community。

## <a name="start-the-installer"></a>啟動安裝程式

下載完成之後，按一下 [執行] 來啟動安裝程式。

![Visual Studio 2019 安裝程式](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>選擇工作負載

Visual Studio 可以用於許多不同種類的開發，且工作負載讓您輕鬆就能下載您想要建置的應用程式類型所需的所有項目。 目前請選擇 [ASP.NET 與網頁程式開發] 和 [.NET Core 跨平台開發] 工作負載。 您稍後一律可重新啟動安裝程式，以安裝其他工作負載和元件。

![Visual Studio 2019 選擇工作負載](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>安裝

按一下 [安裝] 並讓安裝程式下載並安裝 Visual Studio。

## <a name="run-visual-studio-for-the-first-time"></a>第一次執行 Visual Studio

當安裝程式完成時，Visual Studio 應該會自動啟動。 系統可能會提示您登入，這樣提供一些很棒的相關功能，但目前您可以選擇稍後再登入。 接下來，您可以選擇佈景主題和開發設定。 設定這些選項之後，您就能啟動您的第一個專案。 按一下 [建立新專案]，然後選擇 [ASP.NET Core Web 應用程式]。

![Visual Studio 2019 建立新的 ASP.NET Core Web 應用程式專案](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>探索 ASP.NET Core 專案類型

您可以選擇您的專案名稱和位置，然後挑選 [建立]。 現在，選擇您 ASP.NET Core 應用程式要使用的範本。 您可選擇下列選項：

- 空白。 空白專案範本可讓您從最初開始。
- API。 最適合 Web API。
- Web 應用程式。 使用 Razor Pages 建置的標準 ASP.NET Core Web 應用程式。
- Web 應用程式 (Model-View-Controller)。 使用 Model-View-Controller 模式的標準 ASP.NET Core Web 應用程式。
- Angular。
- React.js。
- React.js / Redux。
- Razor 類別庫。 用於在專案之間共用 Razor 資產。

請留意到，對於大部分專案範本，您也可以選取方塊來選擇啟用 Docker 支援。 您也可以按一下 [變更驗證] 按鈕來新增驗證資源。 您可以在該處選擇：

- 無驗證。
- 個別使用者帳戶。 這些都儲存在本機或以 Azure 為基礎的資料庫。
- 公司或學校帳戶公司或學校帳戶。 此選項會使用 Active Directory、Azure AD 或 Microsoft 365 進行驗證。
- Windows 驗證。 適合內部網路應用程式。

選取不含驗證的標準 Web 應用程式範本，然後按一下 [ **建立**]。

![Visual Studio 2019 選擇 ASP.NET Core 專案選項](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>下一步

在下一個影片中，您將會深入了解您的第一個 ASP.NET Core 專案。

[教學課程：建立您的第一個 ASP.NET Core Web 應用程式](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>另請參閱

- [教學課程：開始使用 c # 和 ASP.NET Core](tutorial-aspnet-core.md) 無影片逐步解說的更詳細教學課程
