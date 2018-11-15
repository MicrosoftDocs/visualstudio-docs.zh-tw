---
title: 啟用 ASP.NET 應用程式的偵錯 |Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/18
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 41da2eb360bac4c50f85bd908f980f5ee3c1d141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813416"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>偵錯在 Visual Studio 中的 ASP.NET 或 ASP.NET Core 應用程式

您可以偵錯 Visual Studio 中的 ASP.NET 和 ASP.NET Core 應用程式。 ASP.NET 與 ASP.NET Core，程序會不同，不論您它在執行 IIS Express 或本機 IIS 伺服器。 

>[!NOTE]
>下列步驟和設定僅適用於偵錯在本機伺服器上的應用程式。 偵錯應用程式上遠端 IIS 伺服器會使用**附加至處理序**，並忽略這些設定。 如需詳細資訊和遠端偵錯的 ASP.NET 應用程式，在 IIS 上的指示，請參閱 <<c0> [ 在 IIS 電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)或是[在執行 IIS 的遠端電腦上遠端偵錯的 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。

隨附於 Visual Studio 內建的 IIS Express 伺服器。 IIS Express 是針對 ASP.NET 和 ASP.NET Core 專案的預設偵錯伺服器，並且已預先設定。 這是適用於初始的偵錯及測試與偵錯，最簡單的方式。 

您也可以偵錯 ASP.NET 或 ASP.NET Core 應用程式在本機 IIS 伺服器 （版本 8.0 或更新版本） 上的執行應用程式設定。 若要偵錯在本機 IIS，您必須符合下列需求： 

<a name="iis"></a>
- 選取 **開發階段 IIS 支援**時安裝 Visual Studio。 (如果有必要，請重新執行 Visual Studio 安裝程式，請選取**修改**，並新增此元件。)
- 以系統管理員身分執行 Visual Studio。 
- 安裝並正確設定與 ASP.NET 和/或 ASP.NET Core 的適當版本的 IIS。 如需詳細資訊和指示，請參閱 < [IIS 8.0 使用 ASP.NET 3.5 和 ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或是[使用 IIS 的 Windows 上裝載 ASP.NET Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index)。
- 請確定應用程式在 IIS 上執行無誤。

## <a name="debug-aspnet-apps"></a>偵錯 ASP.NET 應用程式 

IIS Express 是預設值，並且已預先設定。 如果您要偵錯在本機 IIS，請確定您符合[進行偵錯的本機 IIS 需求](#iis)。 

1. 選取 Visual Studio 中的 ASP.NET 專案**方案總管**，按一下 **屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。
   
1. 選取 [ **Web** ] 索引標籤。
   
1. 在 **屬性**窗格下方**伺服器**， 
   - 適用於 IIS Express，請選取**IIS Express**從下拉式清單。
   - 本機 IIS，
     1. 選取 **本機 IIS**從下拉式清單。
     1. 旁**專案 URL**欄位中，選取**建立虛擬目錄**，如果您還沒有設定 IIS 中的應用程式。
   
1. 底下**偵錯工具**，選取**ASP.NET**。
   
   ![ASP.NET 偵錯工具設定](media/dbg-aspnet-enable-debugging2.png "ASP.NET 偵錯工具設定")
   
1. 使用**檔案** > **儲存選取項目**或是**Ctrl**+**S**儲存任何變更。 
   
1. 若要偵錯應用程式，在您的專案，請上一些程式碼中設定中斷點。 在 Visual Studio 工具列中，請確定組態設為**偵錯**，而且您想要在瀏的覽器會出現在**IIS Express (\<瀏覽器名稱 >)** 或**本機 IIS (\<瀏覽器名稱 >)** [模擬器] 欄位中。 
   
1. 若要開始偵錯，請選取**IIS Express (\<瀏覽器名稱 >)** 或是**本機 IIS (\<瀏覽器名稱 >)** 工具列中，選取 **開始偵錯**從**偵錯**功能表，或是按下**F5**。 偵錯工具會在中斷點暫停。 如果偵錯工具無法叫用中斷點，請參閱[疑難排解偵錯](#troubleshoot-debugging)。

## <a name="debug-aspnet-core-apps"></a>偵錯 ASP.NET Core 應用程式 

IIS Express 是預設值，並且已預先設定。 如果您要偵錯在本機 IIS，請確定您符合[進行偵錯的本機 IIS 需求](#iis)。 

1. 選取 Visual Studio 中的 ASP.NET Core 專案**方案總管**，按一下 **屬性**圖示，並按下**Alt**+**Enter**，或以滑鼠右鍵按一下並選擇 **屬性**。

1. 選取 [偵錯] 索引標籤。
   
1. 在 [**屬性**窗格中下, 一步]**設定檔**， 
   - 適用於 IIS Express，請選取**IIS Express**從下拉式清單。
   - 本機 iis，請從下拉式清單中，選取應用程式名稱，或選取**的新**中建立新的設定檔名稱，並選取**確定**。
   
1. 旁**啟動**，選取**IIS Express**或是**IIS**從下拉式清單。 
   
1. 請確定**啟動瀏覽器**已選取。
   
1. 底下**環境變數**，請確定**ASPNETCORE_ENVIRONMENT**存在且值為**開發**。 如果沒有，請選取**新增**並將它新增。
   
   ![ASP.NET Core 偵錯工具設定](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET 核心偵錯工具設定")
   
1. 使用**檔案** > **儲存選取項目**或是**Ctrl**+**S**儲存任何變更。 
   
1. 若要偵錯應用程式，在您的專案，請上一些程式碼中設定中斷點。 在 Visual Studio 工具列中，請確定組態設為**偵錯**，以及**IIS Express**，或新的 IIS 設定檔名稱，會出現在 [模擬器] 欄位。 
   
1. 若要開始偵錯，請選取**IIS Express**或是 **\<IIS 設定檔名稱 >** 工具列中，選取**開始偵錯**從**偵錯**功能表，或是按下**F5**。 偵錯工具會在中斷點暫停。 如果偵錯工具無法叫用中斷點，請參閱[疑難排解偵錯](#troubleshoot-debugging)。

## <a name="troubleshoot-debugging"></a>疑難排解 偵錯

如果本機 IIS 偵錯無法繼續到中斷點時，請遵循下列步驟進行疑難排解。 

1. 從 IIS 中，啟動 web 應用程式，並確定它能正確執行。 將執行的 web 應用程式。
   
2. 從 Visual Studio 中，選取**偵錯 > připojit k procesu**或按**Ctrl**+**Alt**+**P**，及連接到 ASP.NET 或 ASP.NET Core 的處理序 (通常**w3wp.exe**或是**dotnet.exe**)。 如需詳細資訊，請參閱 < [připojit k procesu](attach-to-running-processes-with-the-visual-studio-debugger.md)並[如何尋找 ASP.NET 處理序名稱](how-to-find-the-name-of-the-aspnet-process.md)。

如果您可以連接，並使用叫用中斷點**připojit k procesu**，但不是使用**偵錯** > **開始偵錯**或**F5**，設定是在專案屬性中可能不正確。 如果您使用主機檔案，請確定也正確設定。

## <a name="configure-debugging-in-the-webconfig-file"></a>設定 web.config 檔案中的偵錯  

ASP.NET 專案具有*web.config*檔案依預設，其中包含這兩個應用程式設定和啟動資訊，包括偵錯設定。 *Web.config*必須正確設定檔案，進行偵錯。 **屬性**先前各節的更新中的設定*web.config*檔案，但您也可以設定它們以手動方式。 

> [!NOTE]
> ASP.NET Core 專案一開始不會*web.config*檔案，但使用*appsettings.json*並*launchSettings.json*應用程式設定和啟動的檔案資訊。 部署應用程式會建立*web.config*檔案或檔案在專案中，但它們通常不包含偵錯資訊。

> [!TIP]
> 您的部署程序可能會更新*web.config*設定，然後再嘗試偵錯，請務必*web.config*已針對偵錯。
  
**若要手動設定*web.config*檔案進行偵錯：**

1. 在 Visual Studio 中，開啟 ASP.NET 專案的*web.config*檔案。  
  
2. *Web.config*是一個 XML 檔案，因此會包含巢狀標記所標記的區段。 找出`configuration/system.web/compilation`一節。 (如果`compilation`項目不存在，請予以建立。)
  
3. 請確定`debug`屬性中`compilation`元素設定為`true`。 (如果`compilation`項目不包含`debug`屬性、 將它加入，然後將它設定為`true`。) 
  
   如果您使用本機 IIS，而不預設的 IIS Express 伺服器，請確定`targetFramework`屬性中的值`compilation`項目符合 IIS 伺服器上的架構。
  
   `compilation`項目*web.config*檔案應該看起來如下列範例所示：

   > [!NOTE]
   > 此範例中為 partial *web.config*檔案。 通常其他 XML 中的章節`configuration`並`system.web`項目，和`compilation`項目也可能包含其他屬性和項目。
  
   ```xml
   <configuration>  
      ...  
      <system.web>  
          <compilation  debug="true"  targetFramework="4.6.1" ... > 
             ...  
          </compilation>  
      </system.web>  
   </configuration>  
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 自動偵測到的任何變更*web.config*檔案，並套用新的組態設定。 您不需要重新啟動電腦或 IIS 伺服器，才能讓變更生效。  
  
網站可以使用包含數個虛擬目錄和子目錄*web.config*中每個檔案。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式會繼承組態設定的來源*web.config* URL 路徑中較高層級的檔案。 階層*web.config*檔案設定會套用到所有[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]其下方階層中的應用程式。 在中設定不同的組態*web.config*階層中較低的檔案會覆寫較高的檔案中的設定。  
  
比方說，如果您指定`debug="true"`中<em>www.microsoft.com/aaa/web.config</em>，在任何應用程式*aaa*資料夾或任何子資料夾中*aaa*會繼承該設定，但如果其中一個這些應用程式會有其專屬的設定覆寫*web.config*檔案。  
  
## <a name="publish-in-debug-mode-using-the-file-system"></a>在偵錯模式中使用檔案系統發佈

有不同的方式將應用程式發行至 IIS。 這些步驟顯示如何建立和部署使用檔案系統的發行設定檔的偵錯。 若要這樣做，您必須執行 Visual Studio 系統管理員身分。 

> [!IMPORTANT]
> 如果您變更您的程式碼或重建時，您必須重複下列步驟來重新發行。 

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案，然後選擇**發佈**。

3. 選擇**IIS、 FTP 等等**然後按一下**發佈**。

    ![發行至 IIS](media/dbg-aspnet-local-iis.png "發行至 IIS")

4. 在  **CustomProfile**  對話方塊中，如**發行方法**，選擇 **檔案系統**。

5. 針對**目標位置**，選取**瀏覽**(**...**).
   
   - ASP.NET 中，選取**本機 IIS**，選取您為應用程式中建立的網站，然後選取**開啟**。
     
     ![發行至 IIS 的 ASP.NET](media/dbg-aspnet-local-iis1.png "發行至 IIS 的 ASP.NET")
     
   - 適用於 ASP.NET Core 中，選取**檔案系統**，選取您的應用程式中設定，然後選取的資料夾**開啟**。

1. 選取 [下一步]。 

1. 底下**組態**，選取**偵錯**從下拉式清單。

1. 選取 [儲存]。

1. 中**發佈** 對話方塊中，請確定**CustomProfile** （或您剛才建立的設定檔名稱） 隨即出現，並**LastUsedBuildConfiguration**設為**偵錯**。 

1. 選取 [發行]。

    ![發行至 IIS](media/dbg-aspnet-local-iis-select-site.png "發行至 IIS")

> [!IMPORTANT]
> 偵錯模式，可大幅減少您的應用程式的效能。 為了達到最佳效能，設定`debug="false"`中*web.config*和指定的發行組建，當您部署生產應用程式或進行效能度量。  

## <a name="see-also"></a>另請參閱  
[ASP.NET 偵錯： 系統需求](aspnet-debugging-system-requirements.md)   
[如何： 執行背景工作處理序，使用者帳戶](how-to-run-the-worker-process-under-a-user-account.md)   
[如何： 尋找 ASP.NET 處理序的名稱](how-to-find-the-name-of-the-aspnet-process.md)   
[偵錯已部署的 web 應用程式](debugging-deployed-web-applications.md)   
[逐步解說： 偵錯 web form](walkthrough-debugging-a-web-form.md)   
[如何： 偵錯 ASP.NET 例外狀況](how-to-debug-aspnet-exceptions.md)   
[偵錯 web 應用程式： 錯誤和疑難排解](debugging-web-applications-errors-and-troubleshooting.md)
  
