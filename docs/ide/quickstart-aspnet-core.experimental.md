---
title: 使用 Visual Studio 在 C# 中建立 ASP.NET Core Web 應用程式
description: 了解如何在 Visual Studio 中使用 C# 與 ASP.NET Core 逐步建立簡單的 Hello World Web 應用程式。
ms.custom: mvc
ms.date: 09/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 53bed90ea686897c2a668ddbc64c60a95c8edfe8
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028932"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 ASP.NET Core Web 應用程式

在這個 5-10 分鐘的 Visual Studio 使用方式簡介中，您將會使用 ASP.NET 專案範本與 C# 程式設計語言建立簡單的 "Hello World" Web 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，您將建立 ASP.NET Core Web 應用程式專案。 方式如下：

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [ASP.NET Core Web 應用程式]。 接著，將您的檔案命名為 `HelloWorld` 並選擇 [確定]。

1. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，確認上方的下拉式功能表出現 [ASP.NET Core 2.0]。 接著，選擇 [Web 應用程式]，然後選擇 [確定]。

   ![檢視示範如何在 Visual Studio 中建立 C# ASP.NET Core 專案的動畫 .gif 檔案](../ide/media/csharp-aspnet-animated-create-project.gif)

   Visual Studio 隨即開啟您的專案檔。

   > [!NOTE]
   > 如果您看不到 [.NET Core] 專案範本類別，請選擇左窗格中的 [開啟 Visual Studio 安裝程式] 連結。
   >
   > ![從 [新增專案] 對話方塊開啟 Visual Studio 安裝程式](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。
   >
   > ![VS 安裝程式中的 ASP.NET 工作負載](../ide/media/quickstart-aspnet-workload.png)
   >
   > (您可能必須關閉 Visual Studio 才能繼續安裝新的工作負載)。

## <a name="create-and-run-the-app"></a>建立並執行應用程式

接下來，您會建立並執行 "Hello World" Web 應用程式。 方式如下：

1. 在 Visual Studio 的 [方案總管] 中，展開 [Pages] 資料夾。 然後，選擇 [About.cshtml]。

   ![從方案總管選擇 About.cshtml 檔案](../ide/media/csharp-aspnet-about-page-html-file.png)

   該檔案是對應到 Web 應用程式 (在網頁瀏覽器中執行) 中名為 [關於] 的頁面。

   ![Web 應用程式中的 [關於] 頁面](../ide/media/csharp-aspnet-about-page.png)

1. 在 Visual Studio 程式碼編輯器中，將 "additional information" 文字變更為 "**Hello World!**"。

1. 在 [方案總管] 中，展開 [About.cshtml]，然後選擇 **About.cshtml.cs**。

1. 將 [應用程式描述] 訊息文字變更為「**什麼是我的訊息?**」。

1. 選擇 [IIS Express] 或按 **Ctrl**+**F5** 執行應用程式，並在網頁瀏覽器中開啟它。

   ![檢視示範如何在 Visual Studio 中建立並執行 C# ASP.NET Core Web 應用程式的動畫 .gif 檔案](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > 如果您收到錯誤訊息指出「無法連接到網頁伺服器 'IIS Express'」，請關閉 Visual Studio，然後使用右鍵或操作功能表中的 [以系統管理員身分執行] 選項來開啟它。 接著，再次執行應用程式。

1. 在網頁瀏覽器中，確認 [關於] 頁面包含更新的文字。

1. 關閉網頁瀏覽器。

恭喜您完成此快速入門！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE (整合式開發環境)。

## <a name="next-steps"></a>後續步驟

若要深入了解，請繼續進行下列教學課程：

> [!div class="nextstepaction"]
> [Visual Studio 中的 C# 和 ASP.NET 使用者入門](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>另請參閱

[使用 Visual Studio 將 Web 應用程式發行到 Azure App Service](..//deployment/quickstart-deploy-to-azure.md)
