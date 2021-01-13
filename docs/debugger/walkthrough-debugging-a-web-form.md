---
title: Web Form 的 Debug |Microsoft Docs
description: 遵循逐步解說，以瞭解如何將 ASP.NET Web 應用程式 (Web Form) ，包括如何設定中斷點和檢查變數。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007a63ea16ab044292f451d8d9c427f4358e3f13
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148217"
---
# <a name="walkthrough-debugging-a-web-form"></a>逐步解說：偵錯 Web 表單
這個逐步解說中的步驟將示範如何偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式 (也稱為 Web Form)。 會向您示範如何啟動及停止執行、設定中斷點，以及在 [監看式] 視窗中檢查變數。

> [!NOTE]
> 若要完成本逐步解說，您在伺服器電腦中必須具有系統管理員權限。 根據預設，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序 aspnet_wp.exe 或 w3wp.exe 會做為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序執行。 若要對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 進行偵錯，您必須在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 執行的電腦上具有系統管理員權限。 如需詳細資訊，請參閱[系統需求](../debugger/aspnet-debugging-system-requirements.md)。

根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="to-create-the-web-form"></a>若要建立 Web Form

1. 如果您已經開啟方案，請將其關閉。

2. 在 [檔案] 功能表上按一下 [新增]，然後按一下 [網站]。

    [新網站] 對話方塊隨即出現。

3. 在 [範本] 窗格中按一下 **ASP.NET 網站**。

4. 在 [ **位置** ] 行上，從清單中按一下 [ **HTTP** ]，然後在文字方塊中輸入 **http://localhost/WebSite** 。

5. 在 [語言] 清單中，按一下 **Visual C#** 或 **Visual Basic**。

6. 按一下 [確定]。

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 建立新的專案，並顯示預設的 HTML 原始程式碼。 其也會在 IIS 中 [預設的網站] 下方，建立名為 [網站] 的新虛擬目錄。

7. 按一下下邊界的 [設計] 索引標籤。

8. 按一下左邊界的 [工具箱] 索引標籤，或是在 [檢視] 功能表上將其選取。

    [ **工具箱** ] 會開啟。

9. 按一下 [工具箱] 中的 [Button] 控制項，然後將該控制項新增至主要設計介面 Default.aspx。

10. 在 [工具箱] 中按一下 [Textbox] 控制項，然後將該控制項拖曳到主要設計介面 Default.aspx。

11. 在您所放置的 Button 控制項上按兩下。

     這會帶您前往字碼頁：Default.aspx.cs (C#) 或 Default.aspx.vb ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。 資料指標 (Cursor) 應該在 `Button1_Click` 函式中。

12. 在 `Button1_Click` 函式中，加入下列程式碼：

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. 在 [建置] 功能表上，按一下 [建置方案]。

     專案應該會建置而無錯誤。

     現在，您可以開始偵錯。

## <a name="to-debug-the-web-form"></a>若要偵錯 Web Form

1. 在 Default.aspx.cs 或 Default.aspx.vb 視窗中，在與您所加入之文字同一行的左邊界按一下：

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    會出現一個紅點，並且該行上的文字會以紅色反白顯示。 紅點表示中斷點。 當您在偵錯工具下執行應用程式時，偵錯工具會在遇到程式碼的位置中斷執行。 接著您就可以檢視應用程式的狀態並對它進行偵錯。 如需詳細資訊，請參閱[中斷點](/previous-versions/ktf38f66(v=vs.100))。

2. 在 **[偵錯]** 功能表上，按一下 **[開始偵錯]** 。

3. [未啟用偵錯] 對話方塊隨即出現。 選取 [修改 Web.config 檔案以啟用偵錯] 選項，然後按一下 [確定]。

    Internet Explorer 就會啟動並顯示您剛才設計的網頁。

4. 在 Internet Explorer 中按一下按鈕。

    在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，這會帶您前往在 Default.aspx.cs 或 Default.aspx.vb 字碼頁上設定中斷點的程式行位置。 這行程式碼應該會以黃色反白顯示。 您現在可以檢視應用程式中的變數並控制其執行。 您的應用程式會停止執行並等候您的命令。

5. 在 [偵錯] 功能表中按一下 [視窗]，然後按一下 [監看式]，再按一下 [Watch1]。

6. 在 [監看式] 視窗中鍵入 **TextBox1.Text**。

    [監看式] 視窗會顯示 `TextBox1.Text` 變數的值：

   '""'

7. 按一下 [偵錯] 功能表上的 [不進入函式]。

    `TextBox1.Text` 的值會在 [監看式] 視窗中變更，讀取如下：

   `"Button was clicked!"`

8. 在 [偵錯] 功能表上按一下 [繼續]。

9. 在 Internet Explorer 中的該按鈕上再按一下。

     執行會在中斷點再次停止。

10. 在 Default.aspx.cs 或 Default.aspx.vb 視窗中按一下左邊界上的紅點。

     這會移除中斷點。

11. 在 **[偵錯]** 功能表上，按一下 **[停止偵錯]** 。

## <a name="to-attach-to-the-web-form-for-debugging"></a>若要附加至 Web Form 來進行偵錯

1. 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，您可以將偵錯工具附加至執行中的處理序。 若要以最有效的方式來偵錯，請將可執行檔編譯為具有符號 (PDB) 檔案的偵錯版本。

2. 在 Default.aspx.cs 或 Default.aspx.vb 視窗中按一下左邊界，以再次於您加入的程式行設定中斷點：

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. 在 **[偵錯]** 功能表上，按一下 **[啟動但不偵錯]**。

    Web Form 會開始在 Internet Explorer 下執行，但不會附加偵錯工具。

4. 附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序。 如需詳細資訊，請參閱將已 [部署的 Web 應用程式進行調試](../debugger/debugging-deployed-web-applications.md)。

5. 在 Internet Explorer 中按一下您表單上的按鈕。

    在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，您應該在 Default.aspx.cs、Default.aspx.vb 或 Default.aspx 叫用中斷點。

6. 完成偵錯後，請按一下 [偵錯] 功能表上的 [停止偵錯]。

## <a name="see-also"></a>另請參閱

- [ASP.NET 應用程式的偵錯工具](../debugger/how-to-enable-debugging-for-aspnet-applications.md)