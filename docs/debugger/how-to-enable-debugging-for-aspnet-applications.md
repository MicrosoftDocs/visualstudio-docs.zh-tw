---
title: "啟用 ASP.NET 應用程式的偵錯 |Microsoft 文件"
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e3c6dffbd99dbdd91753ce8d06ab139006692089
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>偵錯 Visual Studio 中的 ASP.NET 應用程式

您可以偵錯 ASP.NET 應用程式，從 Visual Studio。

## <a name="requirements"></a>需求

若要依照本主題中的指示，您需要：

- IIS Express，其中包含根據預設，在 Visual Studio 2012 和更新版本

    -或-

- 本機 IIS web 伺服器 （版本 8.0 或更新版本） 已正確設定，且可以執行 ASP.NET 應用程式不會發生錯誤。

如果伺服器位於遠端，必須在遠端電腦上執行遠端偵錯工具。 若要偵錯遠端 IIS 伺服器上，請參閱[IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 

## <a name="configure-debug-settings"></a>設定偵錯設定

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>啟用 ASP.NET 偵錯專案屬性中

1. Visual Studio 中開啟您的 ASP.NET 專案。

2. 中的專案上按一下滑鼠右鍵**方案總管 中**，選擇**屬性**，然後按一下  **Web**  索引標籤。

    針對某些專案類型中，選取**屬性 > 偵錯**改為。 ASP.NET Web Form 專案中，以滑鼠右鍵按一下專案，然後選取**屬性頁 > 起始選項**。
  
3.  在 [偵錯工具] 下，選取 [ASP.NET]  核取方塊。

    ![偵錯工具設定](../debugger/media/dbg-aspnet-enable-debugging.png "偵錯工具設定")

> [!NOTE]
> 如果您建立新的 ASP.NET 專案 (**檔案 > 新的專案**)，偵錯設定已正確設定。

### <a name="enable-debugging-in-the-webconfig-file"></a>Web.config 檔案中啟用偵錯  

若要偵錯 web 應用程式，必須正確設定應用程式的 web.config 檔案。 如果您裝載在 IIS 或 IIS Express 應用程式需要 web.config 檔案。

適用於 ASP.NET Core，應用程式部署 （如果尚不存在） 時，會自動建立 web.config 檔案。

> [!TIP]
> 您的部署程序可能會更新 web.config 設定。 因此之前嘗試偵錯，請確認伺服器上的 web.config 設定。
  
1.  在 Visual Studio 中開啟專案的 web.config 檔案。  
  
    > [!NOTE]  
    > 您無法使用網頁瀏覽器，從遠端存取的 web.config 檔案。 基於安全性原因，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 會設定 Microsoft IIS，以協助防止瀏覽器直接存取 Web.config 檔案。 如果您嘗試使用瀏覽器存取組態檔，您會收到 HTTP 存取錯誤 403 （禁止）。  
  
2.  找到 `configuration/system.web/compilation` 項目。 如果 compilation 項目不存在，請建立它。

    Web.config 是一個 XML 檔案，因此會包含透過標記所標記的巢狀區段。
  
3.  如果 `compilation` 項目未包含 `debug` 屬性，請將屬性加入項目中。  
  
4.  請確定`debug`屬性值設為`true`。  
  
Web.config 檔案應該看起來像下列的範例：

> [!NOTE]
> 這個範例是部分的 web.config 檔案。 Configuration 與 system.web 項目之間通常存在時，就其他的 XML 區段。 Compilation 項目也可能包含其他屬性和項目。
  
#### <a name="example"></a>範例  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

如果您使用外部伺服器而不預設的 IIS Express 伺服器，您也必須確定所`targetFramework`屬性值符合伺服器上的設定。

> [!IMPORTANT]
> 為了達到最佳效能，生產環境應用程式設定為`debug=false`和指定的發行組建，當您建置並發行應用程式。

## <a name="configure-project-settings-for-the-server"></a>設定伺服器的專案設定

偵錯的本機 web 伺服器上，設定專案屬性。 偵錯在遠端伺服器上，依照更詳盡的指示中所述[在 IIS 上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)改為。

1. 在**Web**  索引標籤的 專案屬性中，選取  **IIS Express**或**外部伺服器**下**伺服器**設定。 (針對某些專案類型，這些設定會顯示在**偵錯**改為索引標籤。)

    ![伺服器設定](../debugger/media/dbg-aspnet-server-settings.png "伺服器設定")

    IIS Express 是 ASP.NET 的預設伺服器，和通常不需要任何特殊設定。 這是最簡單的方式偵錯 ASP.NET 應用程式。

    ASP.NET Web Form 專案中，以滑鼠右鍵按一下專案，選擇 **屬性頁 > 起始選項**，並選取 **使用預設 Web 伺服器**或**使用自訂伺服器**(而不是**外部伺服器**)。

    ![Web Form 應用程式的伺服器設定](../debugger/media/dbg-aspnet-server-settings-webforms.png "Web Form 應用程式的伺服器設定")

2. 如果您選擇外部伺服器 （自訂），請輸入正確的 URL 中**專案 URL** (或**基底 URL**) 欄位。

    如果本機 IIS 外部的伺服器，就必須安裝並正確設定 IIS。 例如，必須在 IIS 中設定正確的 ASP.NET 版本。 如需詳細資訊，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。 如果您想要測試部署，以及偵錯，請參閱[部署來測試](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis)。

    如果外部伺服器[遠端](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)相反地，附加至處理序，這些專案不會使用設定偵錯。

## <a name="local-iis-web-server-configure-iis"></a>（本機 IIS web 伺服器）設定 IIS

IIS express，您不需要設定網頁伺服器 （略過這一節）。 IIS Express 被建議用於初始測試。

如果您使用本機 IIS web 伺服器，請遵循下列步驟。

1. 請確定 IIS 已正確安裝。 如需詳細資訊，請參閱[IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)。

    * 請確定您在伺服器上安裝正確的 ASP.NET 版本。 使用 Web Platform Installer (WebPI) 安裝 ASP.NET 4.5 (從 Windows Server 2012 R2 中的 伺服器 節點，選擇 **取得新的 Web 平台元件**ASP.NET 然後搜尋)。 若要安裝 ASP.NET Core，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration)。

    > [!NOTE]
    > 如果您使用 Windows Server 2008 R2，請安裝 ASP.NET 4，改為使用這個命令：

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe ir**

2. 開啟**Internet Information Services (IIS) 管理員**。 (在伺服器管理員 的左窗格中選取**IIS**。 以滑鼠右鍵按一下伺服器，然後選取**網際網路資訊服務 (IIS) 管理員**。)

3. 在下**連線**在左窗格中，移至**網站**。

4. 以滑鼠右鍵按一下 [預設的網站]  節點，並選取 [加入應用程式] 。

5. 設定**別名**欄位設為**MyASPApp**，接受預設的應用程式集區 (**DefaultAppPool**)，並設定**實體路徑**至**C:\inetpub\myNewFolder** （建立應用程式的新資料夾）。

6. 在下**連線**，選取**應用程式集區**。 開啟**DefaultAppPool**和設定應用程式集區欄位的值，是正確的應用程式 （針對 ASP.NET 4.5 使用 ASP.NET 4。 使用**沒有 Managed 程式碼**適用於 ASP.NET Core)。

## <a name="local-iis-web-server-deploy-the-app"></a>（本機 IIS web 伺服器）部署應用程式

IIS express，web 應用程式會自動進行部署時開始偵錯 （略過這一節）。

如果您使用本機 IIS web 伺服器，請遵循下列步驟。 有不同的方式來將您的應用程式發行至 IIS。 在這些步驟中，我們會示範如何建立和使用發行設定檔，讓您可以使用檔案系統。

1. 身為系統管理員，重新啟動 Visual Studio。

    若要部署使用此方法，您需要系統管理員權限。

2. 在 Visual Studio 中，以滑鼠右鍵按一下專案，然後選擇 **發行**(用於 Web Form**發行 Web 應用程式**)。

3. 選擇**IIS，FTP 等**按一下**發行**。

    ![發行至 IIS](../debugger/media/dbg-aspnet-local-iis.png "發行至 IIS")

    Web Form 應用程式中，選擇 **自訂**在 發行 對話方塊中，輸入設定檔名稱，然後選擇 **確定**。

4. 在**發行方法**欄位中，選擇**檔案系統**。

5. 如**目標位置**，按一下 [**瀏覽**] 按鈕。

6. (ASP.NET Core)選擇**檔案系統**並選取您先前建立的應用程式的資料夾。

6. (ASP.NET)選擇**本機 IIS**，並選取您先前建立的然後再按一下網站**開啟**。

    ![發行至 IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "發行至 IIS")

    > [!TIP]
    > 如果您看到訊息指出，網頁伺服器未正確設定，請確定正確的 ASP.NET 版本已安裝 iis。

7. 按一下**下一步**選擇**偵錯**組態。

    > [!NOTE]
    > 如果您部署含發行組態，這會設定`debug=false`伺服器的 web.config 檔案中。

8. 按一下**儲存**來儲存發行設定，然後再按一下**發行**。

    > [!CAUTION]
    >  如果您需要對程式碼或重建的變更，您必須重新發佈，並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。

## <a name="set-a-breakpoint-and-start-debugging"></a>設定中斷點並開始偵錯

1. 在 Visual Studio 中的專案，將執行集合上您知道某些程式碼的中斷點。

2. 若要開始偵錯，請按**F5** (**偵錯 > 開始偵錯**)。

3. 採取動作，執行包含中斷點的程式碼。

    偵錯工具暫停，您用來設定中斷點。

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(本機 IIS)疑難排解： 無法叫用中斷點

1. 從 IIS 啟動 web 應用程式，並確定它能正確執行。 保留執行 web 應用程式。

2. 從 Visual Studio 中，選取**偵錯 > 附加至處理序**並連接到 ASP.NET 處理序 (通常**w3wp.exe**或**dotnet.exe**)。 如需詳細資訊，請參閱[附加至處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。

    如果您可以使用連接**附加至處理序**可以叫用中斷點的行，而無法啟動偵錯使用**F5**，則很可能設定不正確的專案屬性中。 如果您使用的主機檔案，請確認已正確設定。

  
## <a name="robust-programming"></a>穩固程式設計  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 會自動偵測任何 Web.config 檔案變更，並套用新的組態設定。 您不需要重新啟動電腦或重新啟動 IIS 伺服器，變更就會生效。  
  
網站可以包含多個虛擬目錄和子目錄，而 Web.config 檔案可能存在於每一個目錄和子目錄中。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式會繼承 URL 路徑中較高層級之 Web.config 檔案中的設定。 階層式組態檔可讓您同時變更數個 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的設定 (例如，針對階層中其下的所有應用程式)。 不過，如果`debug`設定在階層中較低的檔案中，它會覆寫較高的值。  
  
例如，您可以指定`debug="true"`www.microsoft.com/aaa/Web.config 和任何應用程式中 aaa 資料夾或 aaa 之任何子資料夾會繼承該設定。 因此，如果您[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]www.microsoft.com/aaa/bbb 是應用程式，它會繼承該設定，將任何[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]www.microsoft.com/aaa/ccc、 www.microsoft.com/aaa/ddd，等等中的應用程式。 唯一的例外是其中一個應用程式透過自己的較低 Web.config 檔案來覆寫設定時。  
  
> [!IMPORTANT]
> 啟用偵錯模式會大幅影響效能的程式[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]應用程式。 請務必先停用偵錯模式，再部署發行應用程式或進行效能度量。  
  
## <a name="see-also"></a>請參閱  
[ASP.NET 偵錯： 系統需求](aspnet-debugging-system-requirements.md)   
[如何： 執行背景工作處理序的使用者帳戶](how-to-run-the-worker-process-under-a-user-account.md)   
[如何： 尋找 ASP.NET 處理序的名稱](how-to-find-the-name-of-the-aspnet-process.md)   
[偵錯已部署的 Web 應用程式](debugging-deployed-web-applications.md)   
[逐步解說： 偵錯 Web Form](walkthrough-debugging-a-web-form.md)   
[如何： 偵錯 ASP.NET 例外狀況](how-to-debug-aspnet-exceptions.md)   
[對 Web 應用程式進行偵錯：錯誤和疑難排解](debugging-web-applications-errors-and-troubleshooting.md)
  