---
title: 使用 Visual Studio 在 C# 中建立 ASP.NET Core Web 應用程式
description: 了解如何在 Visual Studio 中使用 C# 逐步建立 ASP.NET Core Web 應用程式。
ms.custom: mvc
ms.date: 07/20/2018
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
ms.openlocfilehash: a64674ae5a902e332ae8b9eb3cbe6a22d09a1133
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380612"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 ASP.NET Core Web 應用程式

在這個 5-10 分鐘的 Visual Studio 使用方式簡介中，您將會使用 ASP.NET 專案範本與 C# 程式設計語言建立簡單的 "Hello World" Web 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，您將建立 ASP.NET Core Web 應用程式專案。 此專案類型隨附建立 Web 應用程式所需的範本檔案，甚至是在您新增任何項目之前便已完備！

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [ASP.NET Core Web 應用程式]。 接著，將您的檔案命名為 `HelloWorld` 並選擇 [確定]。

   ![建立新的 C# ASP.NET Core Web 應用程式專案](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，確認上方的下拉式功能表出現 [ASP.NET Core 2.0]。 接著，選擇 [Web 應用程式]，然後選擇 [確定]。

   ![新增 ASP.NET Core Web 應用程式對話方塊](../ide/media/quickstart-aspnet-core20.png)

Visual Studio 隨即開啟您的專案檔。

## <a name="create-the-app"></a>建立應用程式

1. 在 [方案總管] 中，展開 [頁面] 資料夾，然後選擇 **About.cshtml**。

   ![從方案總管選擇 About.cshtml 檔案](../ide/media/csharp-aspnet-about-page-html-file.png)

   此檔案對應至 Web 應用程式中名為 [關於] 的頁面。

   ![Web 應用程式中的 [關於] 頁面](../ide/media/csharp-aspnet-about-page.png)

   在編輯器中，您將會看到 [關於] 頁面之 [其他資訊] 區域的 HTML 程式碼。

   ![Visual Studio 編輯器中其他資訊區域的 HTML 程式碼](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. 將 [其他資訊] 文字變更為 "**Hello World!**"。

   ![變更 Visual Studio 編輯器中其他資訊區域的預設 HTML 程式碼](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. 在 [方案總管] 中，展開 [About.cshtml]，然後選擇 **About.cshtml.cs**。 (此檔案也對應到您 Web 應用程式中的 [關於] 頁面)。

   ![從方案總管選擇 About.cshtml 檔案](../ide/media/csharp-aspnet-about-page-code-file.png)

   在編輯器中，您將會看到包含 [關於] 頁面之 [應用程式描述] 區域文字的 C# 程式碼。

   ![Visual Studio 編輯器中應用程式描述區域的 C# 程式碼](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. 將 [應用程式描述] 訊息文字變更為「**什麼是我的訊息?**」。

   ![變更 Visual Studio 編輯器中應用程式描述區域的預設訊息文字](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>執行應用程式

1. 按 **Ctrl**+**F5** 執行應用程式，並在網頁瀏覽器中開啟它。

   > [!NOTE]
   > 如果您收到錯誤訊息指出「無法連接到網頁伺服器 'IIS Express'」，請關閉 Visual Studio，然後使用右鍵或操作功能表中的 [以系統管理員身分執行] 選項來開啟它。 接著，再次執行應用程式。

1. 在網頁頂端，選擇 [關於]。

   ![從網頁選取 [關於]](../ide/media/csharp-aspnet-home-page-about.png)

1. 檢視您加入到 [關於] 頁面的更新文字。

   ![檢視包含您加入之文字的已更新 [關於] 頁面](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. 關閉網頁瀏覽器。

恭喜您完成此快速入門！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE (整合式開發環境)。

## <a name="next-steps"></a>後續步驟

若要深入了解，請繼續進行下列教學課程：

> [!div class="nextstepaction"]
> [Visual Studio 中的 C# 和 ASP.NET 使用者入門](tutorial-csharp-aspnet-core.md)
>
> [!div class="nextstepaction"]
> [ASP.NET Core MVC 與 Visual Studio 使用者入門](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)

## <a name="see-also"></a>另請參閱

[使用 Visual Studio 將 Web 應用程式發行到 Azure App Service](..//deployment/quickstart-deploy-to-azure.md)
