---
title: 以 C# 建立 ASP.NET Core Web 應用程式
description: 了解如何在 Visual Studio 中使用 C# 與 ASP.NET Core 逐步建立簡單的 Hello World Web 應用程式。
ms.custom: acquisition, mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 61fc3f0cf1e23dcf0f9e22ed7e10050fb84c9ba6
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308060"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 ASP.NET Core Web 應用程式

在這個 5-10 分鐘的 Visual Studio 使用方式簡介中，您將會使用 ASP.NET 專案範本與 C# 程式設計語言建立簡單的 "Hello World" Web 應用程式。

## <a name="before-you-begin"></a>開始之前

### <a name="install-visual-studio"></a>安裝 Visual Studio

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2022"

如果您尚未安裝 Visual Studio 2022 Preview，請前往 [Visual Studio 2022 preview 下載](https://visualstudio.microsoft.com/vs/preview/vs2022) 頁面，免費進行安裝。

::: moniker-end

### <a name="choose-your-theme-optional"></a>選擇您的佈景主題 (選擇性)

本快速入門包含使用深色佈景主題的螢幕擷取畫面。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](quickstart-personalize-the-ide.md)頁面以了解做法。

## <a name="create-a-project"></a>建立專案

首先，您將建立 ASP.NET Core Web 應用程式專案。 此專案類型隨附建立 Web 應用程式所需的範本檔案，甚至是在您新增任何項目之前便已完備！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [ASP.NET Core Web 應用程式]。 <br/><br/>接著，將您的檔案命名為 `HelloWorld` 並選擇 [確定]。

   ![建立新的 C# ASP.NET Core Web 應用程式專案](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > 如果您看不到 [.NET Core] 專案範本類別，請選擇左窗格中的 [開啟 Visual Studio 安裝程式] 連結。 (根據您的顯示設定，您可能必須捲動才能看到它。)
   >
   > ![從 [新增專案] 對話方塊開啟 Visual Studio 安裝程式](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。
   >
   > ![VS 安裝程式中的 ASP.NET 工作負載](../ide/media/quickstart-aspnet-workload.png)
   >
   > (您可能必須關閉 Visual Studio 才能繼續安裝新的工作負載)。

1. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，從上方的下拉式功能表中選取 [ASP.NET Core 2.1] 接下來，選擇 [Web 應用程式]，然後選擇 [確定]。

   ![新增 ASP.NET Core Web 應用程式對話方塊](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > 如果您沒有看到 [ASP.NET Core 2.1]，請確定您執行的是最新版本的 Visual Studio。 如需如何更新安裝的詳細資訊，請參閱[將 Visual Studio 更新至最新版本](../install/update-visual-studio.md)頁面。

Visual Studio 隨即開啟您的專案檔。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="檢視 [建立新專案] 視窗":::

1. 在 [ **建立新專案** ] 視窗中，從 [語言] 清單中選擇 [ **c #** ]。 接著，從 [平臺] 清單中選擇 [ **Windows** ]，然後從 [專案類型] 清單中選擇 [ **Web** ]。

      套用語言、平臺和專案類型篩選器之後，請選擇 **ASP.NET Core Web 應用程式** 範本，然後選擇 [ **下一步]**。

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="選擇 ASP.NET Core Web 應用程式的 c # 範本":::

   > [!NOTE]
   > 如果您沒有看到 **ASP.NET Core 的 Web 應用程式** 範本，您可以從 [ **建立新專案** ] 視窗進行安裝。 在 [找不到您要找的資料嗎?] 訊息中，選擇 [安裝更多工具和功能] 連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 然後，在 Visual Studio 安裝程式中選擇 **ASP.NET 與網頁程式開發** 工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > 接下來，選擇 Visual Studio 安裝程式中的 [修改] 按鈕。 如果系統出現提示，請儲存您的工作。 接下來，選擇 [繼續] 以安裝工作負載。 然後，返回至「[建立專案](#create-a-project)」程序中的步驟 2。

1. 在 [設定您的新專案] 視窗的 [專案名稱] 方塊中鍵入或輸入 *HelloWorld*。 然後選擇 **[下一步]**。

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="在 [設定新專案] 視窗中，將專案命名為 'MyCoreApp'":::

1. 在 [ **其他資訊** ] 視窗中，確認 [ **.net Core 3.1** ] 出現在頂端的下拉式功能表中。 請注意，您可以勾選方塊來選擇啟用 Docker 支援。 您也可以按一下 [變更驗證] 按鈕，以新增驗證支援。 您可以在該處選擇：
    - None：無驗證。
    - 個別帳戶：這些帳戶儲存在本機或以 Azure 為基礎的資料庫中。
    - Microsoft 身分識別平臺：此選項會使用 Active Directory、Azure AD 或 Microsoft 365 進行驗證。
    - Windows：適用于內部網路應用程式。
    
    讓 [ **啟用 Docker** ] 方塊保持未選取狀態，並針對 [驗證類型] 選取 [ **無** ]。 然後，選取 [Create] \(建立\)。

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="在 [其他資訊] 視窗中，確認已選取 [.NET Core 3.1]，並保留所有預設值":::

   Visual Studio 將會開啟您的新專案。

::: moniker-end

## <a name="create-and-run-the-app"></a>建立並執行應用程式

::: moniker range="vs-2017"

1. 在 [方案總管] 中，展開 [頁面] 資料夾，然後選擇 **About.cshtml**。

   ![Visual Studio 方案總管的螢幕擷取畫面，其中顯示 HelloWorld 專案中的檔案。 展開 [頁面] 資料夾，並選取 []。](../ide/media/csharp-aspnet-about-page-html-file.png)

   該檔案是對應到 Web 應用程式 (在網頁瀏覽器中執行) 中名為 [關於] 的頁面。

   ![Web 應用程式中的 [關於] 頁面](../ide/media/csharp-aspnet-about-page.png)

   在編輯器中，您將會看到 [關於] 頁面之 [其他資訊] 區域的 HTML 程式碼。

   ![Visual Studio 編輯器中其他資訊區域的 HTML 程式碼](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. 將 [其他資訊] 文字變更為 "**Hello World!**"。

   ![變更 Visual Studio 編輯器中其他資訊區域的預設 HTML 程式碼](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. 在 [方案總管] 中，展開 [About.cshtml]，然後選擇 **About.cshtml.cs**。 (此檔案也對應到您 Web 瀏覽器中的 [關於] 頁面)。

   ![Visual Studio 方案總管的螢幕擷取畫面，其中顯示 HelloWorld 專案中的檔案。 關於. cshtml 已展開，且已選取 [...]。](../ide/media/csharp-aspnet-about-page-code-file.png)

   在編輯器中，您將會看到包含 [關於] 頁面之 [應用程式描述] 區域文字的 C# 程式碼。

   ![Visual Studio 編輯器中應用程式描述區域的 C# 程式碼](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. 將 [應用程式描述] 訊息文字變更為「**What's my message?**」。

   ![變更 Visual Studio 編輯器中應用程式描述區域的預設訊息文字](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. 選擇 [IIS Express] 或按 **Ctrl**+**F5** 執行應用程式，並在網頁瀏覽器中開啟它。

   ![選取 Visual Studio 中的 [IIS Express] 按鈕](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > 如果您收到的錯誤訊息指出「無法連線到 Web 伺服器 'IIS Express'」，或是提及 SSL 憑證，請關閉 Visual Studio。 接下來，從右鍵操作功能表使用 [以系統管理員身分執行] 選項來開啟 Visual Studio。 接著，再次執行應用程式。

1. 在網頁瀏覽器中，確認 [關於] 頁面包含更新的文字。

   ![檢視包含您所做變更的 [關於] 頁面](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. 關閉網頁瀏覽器。

### <a name="review-your-work"></a>檢閱工作

檢視以下動畫以檢查您在上一節中完成的工作。

  ![檢視示範如何在 Visual Studio 中建立並執行簡單 C# ASP.NET Core Web 應用程式的動畫 .gif 檔案](../ide/media/csharp-aspnet-animated-hello-world.gif)

恭喜您完成此快速入門！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE (整合式開發環境)。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [ **方案總管** 中，展開 [ **Pages** ] 資料夾，然後選擇 [ **Index**]。

   ![從方案總管選擇 [索引]。](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   此檔案對應至 web 應用程式中名為 **Home** 的頁面，該頁面會在網頁瀏覽器中執行。

   ![Web 應用程式中的 [關於] 頁面](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   在編輯器中，您會看到顯示在 **首頁** 上之文字的 HTML 程式碼。

   ![Visual Studio 編輯器中首頁的索引 cshtml 檔案中的 HTML 程式碼](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. 變更 [歡迎使用] 文字以讀取 "**Hello World！**"。

   ![在 [Visual Studio 編輯器] 中，變更顯示為 [歡迎使用] Hello World 的預設 HTML 程式碼](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. 選擇 [IIS Express] 或按 **Ctrl**+**F5** 執行應用程式，並在網頁瀏覽器中開啟它。

   ![選取 Visual Studio 中的 [IIS Express] 按鈕](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > 如果您收到的錯誤訊息指出「無法連線到 Web 伺服器 'IIS Express'」，或是提及 SSL 憑證，請關閉 Visual Studio。 接下來，從右鍵操作功能表使用 [以系統管理員身分執行] 選項來開啟 Visual Studio。 接著，再次執行應用程式。

1. 在網頁瀏覽器中，確認 **首頁** 是否包含更新的文字。

   ![查看包含您所做變更的更新首頁](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. 關閉網頁瀏覽器。

::: moniker-end

## <a name="next-steps"></a>後續步驟

若要深入了解，請繼續下列教學課程：

> [!div class="nextstepaction"]
> [Visual Studio 中的 C# 和 ASP.NET 使用者入門](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>另請參閱

[使用 Visual Studio 將 Web 應用程式發佈至 Azure App Service](../deployment/quickstart-deploy-to-azure.md)
