---
title: 使用 Visual Studio 在 C# 中建立 ASP.NET Core Web 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 10/10/2017
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e8e7838d48f974caeb67ed09c193aaee4633d781
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>快速入門：使用 Visual Studio 建立您的第一個 ASP.NET Core Web 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立簡單的 C# ASP.NET Core Web 應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

## <a name="create-a-project"></a>建立專案

首先，您將建立 ASP.NET Core Web 應用程式專案。 在新增任何項目之前，專案類型隨附的範本檔案可構成功能性 Web 應用程式！

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [ASP.NET Web 應用程式]，然後選擇 [確定]。

     如果您看不到 [.NET Core] 專案範本類別，請選擇左窗格中的 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

     ![VS 安裝程式中的 ASP.NET 工作負載](../ide/media/quickstart-aspnet-workload.png)

1. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，從上方的下拉式功能表中選取 [ASP.NET Core 2.0]  (如果您在清單中看不到 [ASP.NET Core 2.0]，請遵循應該出現在接近對話方塊頂端之黃色列中的 [下載] 連結來進行安裝)。選擇 [ **確定**]。

   ![新增 ASP.NET Core Web 應用程式對話方塊](../ide/media/quickstart-aspnet-core20.png)

## <a name="explore-the-ide"></a>探索 IDE

1. 在方案總管工具列中，展開 [頁面] 資料夾，然後選擇 **About.cshtml** 以在編輯器中予以開啟。 此檔案對應至 Web 應用程式中稱為 [關於] 的頁面。

1. 在編輯器中，選擇 `AboutModel`，然後按 **F12**，或選擇操作 (右鍵) 功能表中的 [移至定義]。 此命令會將您帶到 `AboutModel` C# 類別的定義。

   ![移至定義操作功能表](../ide/media/quickstart-aspnet-gotodefinition.png)

1. 接下來，我們將會使用簡單捷徑來清除檔案頂端的 `using` 指示詞。 選擇任何灰色 using 指示詞，而且[快速動作](../ide/quick-actions.md)燈泡會顯示在插入點正下方或左邊界中。 選擇燈泡，然後選擇 [移除不必要的 Using]。

     不必要的 using 會從檔案中刪除。

1. 在 `OnGet()` 方法中，將主體變更為下列程式碼：

 ```csharp
 public void OnGet()
 {
     string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
 }
 ```

1. 您會看到兩個波浪底線出現在 [環境] 和 [字串] 下方，因為這些類型不在範圍內。 開啟 [錯誤清單] 工具列，以查看該處所列的相同錯誤  (如果您看不到 [錯誤清單] 工具列，請從頂端功能表列中選擇 [檢視] > [錯誤清單])。

   ![錯誤清單](../ide/media/quickstart-aspnet-errorlist.png)

1. 在編輯器視窗中，將游標放在包含錯誤的任一行上方，然後選擇左邊界的 [快速動作] 燈泡。 從下拉式功能表中，選擇 **using System;** 將此指示詞新增至檔案頂端，並解決錯誤。

## <a name="run-the-application"></a>執行應用程式

1. 按 **Ctrl**+**F5** 執行應用程式，並在網頁瀏覽器中開啟它。

1. 在網站頂端，選擇 [關於]，以查看您在 [關於] 頁面的 `OnGet()` 方法中新增目錄訊息。

1. 關閉網頁瀏覽器。

> [!NOTE]
> 如果您收到錯誤訊息指出「無法連接到 Web 伺服器 'IIS Express'」，請關閉 Visual Studio，然後以滑鼠右鍵按一下或開啟快顯功能表，使用 [以系統管理員身分執行] 選項開啟它。 接著，再次執行應用程式。

恭喜您完成此快速入門！ 我們希望您更了解 Visual Studio IDE。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程] 一節中的教學課程。

## <a name="next-steps"></a>後續步驟
恭喜您完成此快速入門！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE。 若要深入了解，請繼續下列教學課程。

> [!div class="nextstepaction"]
> [Visual Studio 中的 C# 和 ASP.NET 使用者入門](tutorial-csharp-aspnet-core.md)
