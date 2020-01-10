---
title: 啟用 ASP.NET apps 的偵錯工具 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911344"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio 中的 Debug ASP.NET 或 ASP.NET Core 應用程式

您可以在 Visual Studio 中，對 ASP.NET 和 ASP.NET Core 應用程式進行 debug。 此程式在 ASP.NET 和 ASP.NET Core 之間有所不同，不論您是在 IIS Express 還是本機 IIS 伺服器上執行，都是如此。

>[!NOTE]
>下列步驟和設定僅適用于在本機伺服器上的偵錯工具。 在遠端 IIS 伺服器上的偵錯工具會使用 [**附加至進程**]，並忽略這些設定。 如需在 IIS 上進行遠端 ASP.NET 應用程式的詳細資訊和指示，請參閱[iis 電腦上的遠端 debug ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)或遠端[iis 電腦上的遠端 debug ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。

內建的 IIS Express 伺服器隨附于 Visual Studio。 IIS Express 是 ASP.NET 和 ASP.NET Core 專案的預設 debug 伺服器，而且已預先設定。 這是最簡單的偵錯工具方式，非常適合進行初始的調試和測試。

您也可以在設定為執行應用程式的本機 IIS 伺服器（版本8.0 或更高版本）上，進行 ASP.NET 或 ASP.NET Core 的應用程式的偵錯工具。 若要在本機 IIS 上進行調試，您必須符合下列需求：

<a name="iis"></a>
- 安裝 Visual Studio 時，請選取 [**開發階段 IIS 支援**]。 （如有必要，請重新執行 Visual Studio 安裝程式，選取 [**修改**]，然後新增此元件）。
- 正在以系統管理員身分執行 Visual Studio。
- 使用適當的 ASP.NET 和/或 ASP.NET Core 版本安裝並正確設定 IIS。 如需詳細資訊和指示，請參閱[使用 ASP.NET 3.5 和 ASP.NET 4.5 的 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)或[WINDOWS 上使用 iis 的主機 ASP.NET Core](/aspnet/core/host-and-deploy/iis/index)。
- 請確定應用程式會在 IIS 上執行，而不會發生錯誤。

## <a name="debug-aspnet-apps"></a>ASP.NET 應用程式的 Debug

IIS Express 是預設值，而且已預先設定。 如果您要在本機 IIS 上進行偵錯工具，請確定您符合[本機 iis 偵錯工具的需求](#iis)。

1. 在 Visual Studio**方案總管**中選取 [ASP.NET] 專案，然後按一下 [**屬性**] 圖示，按**Alt**+**enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [ **Web** ] 索引標籤。

1. 在 [**屬性**] 窗格中的 [**伺服器**] 底下，
   - 針對 IIS Express，請從下拉式清單中選取 [ **IIS Express** ]。
   - 若為本機 IIS，
     1. 從下拉式清單中選取 [**本機 IIS** ]。
     1. 在 [**專案 URL** ] 欄位旁，如果您尚未在 IIS 中設定應用程式，請選取 [**建立虛擬目錄**]。

1. 在 [**調試**程式] 下，選取 [ **ASP.NET**]。

   ![ASP.NET 偵錯工具設定](media/dbg-aspnet-enable-debugging2.png "ASP.NET 偵錯工具設定")

1. 使用 **[** 檔案] > **儲存選取的專案**，或按**Ctrl**+**S**以儲存任何變更。

1. 若要在您的專案中進行應用程式的「偵測」，請設定某些程式碼的中斷點。 在 [Visual Studio] 工具列中，確定設定為 [ **Debug**]，而您想要的瀏覽器會出現在 [模擬器] 欄位的**IIS Express （\<瀏覽器名稱 >）** 或**本機 IIS （\<瀏覽器名稱 >）** 中。

1. 若要開始進行調試，請選取工具列中的 **[IIS Express （\<瀏覽器名稱 >）** ] 或 [**本機 IIS （\<瀏覽器名稱 >）** ]，從 [**調試**] 功能表中選取 [**開始調試**]，或按**F5**。 偵錯工具會在中斷點暫停。 如果偵錯工具無法叫用中斷點，請參閱[疑難排解調試](#troubleshoot-debugging)程式。

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core 應用程式的 Debug

IIS Express 是預設值，而且已預先設定。 如果您要在本機 IIS 上進行偵錯工具，請確定您符合[本機 iis 偵錯工具的需求](#iis)。

1. 在 Visual Studio**方案總管**中選取 [ASP.NET Core] 專案，然後按一下 [**屬性**] 圖示，按**Alt**+**enter**鍵，或按一下滑鼠右鍵並選擇 [**屬性**]。

1. 選取 [偵錯] 索引標籤。

1. 在 [**屬性**] 窗格中的 [**設定檔**] 旁，
   - 針對 IIS Express，請從下拉式清單中選取 [ **IIS Express** ]。
   - 若為本機 IIS，請從下拉式清單中選取應用程式名稱，或選取 [**新增**]，建立新的設定檔名稱，然後選取 **[確定]** 。

1. 在 [**啟動**] 旁，從下拉式清單中選取 [ **IIS Express** ] 或 [ **IIS** ]。

1. 請確定已選取 [**啟動瀏覽器**]。

1. 在 [**環境變數**] 下，確定**ASPNETCORE_ENVIRONMENT**存在，且具有 [**開發**] 的值。 如果沒有，請選取 [**新增**]，並將它加入。

   ![ASP.NET Core 偵錯工具設定](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core 偵錯工具設定")

1. 使用 **[** 檔案] > **儲存選取的專案**，或按**Ctrl**+**S**以儲存任何變更。

1. 若要在您的專案中進行應用程式的「偵測」，請設定某些程式碼的中斷點。 在 [Visual Studio] 工具列上，確定 [設定] 已設為 [ **Debug**]，而 [ **IIS Express**] 或新的 IIS 設定檔名稱會出現在 [模擬器] 欄位中。

1. 若要開始進行調試，請選取工具列中的**IIS Express**或 **\<IIS 設定檔名稱 >** ，從 **[調試**] 功能表中選取 [**開始調試**]，或按**F5**。 偵錯工具會在中斷點暫停。 如果偵錯工具無法叫用中斷點，請參閱[疑難排解調試](#troubleshoot-debugging)程式。

## <a name="troubleshoot-debugging"></a>針對調試進行疑難排解

如果本機 IIS 調試錯無法對中斷點進行，請遵循下列步驟進行疑難排解。

1. 從 IIS 啟動 web 應用程式，並確定它能正確執行。 讓 web 應用程式保持執行狀態。

2. 從 Visual Studio 選取  **Debug > 附加至進程**，或按**Ctrl**+**Alt**+**P**，然後連接到 ASP.NET 或 ASP.NET Core 進程（通常是**w3wp.exe .exe**或**dotnet**）。 如需詳細資訊，請參閱[附加至進程](attach-to-running-processes-with-the-visual-studio-debugger.md)和[如何尋找 ASP.NET 進程的名稱](how-to-find-the-name-of-the-aspnet-process.md)。

如果您可以使用 [**附加至進程**] 來連接並叫用中斷點，但不是使用**Debug** > **開始進行調試**程式或**F5**，則在專案屬性中的設定可能不正確。 如果您使用 HOSTS 檔案，請確定它也已正確設定。

## <a name="configure-debugging-in-the-webconfig-file"></a>在 web.config 檔案中設定調試

ASP.NET 專案預設會有*web.config*檔案，其中包含應用程式設定和啟動資訊，包括 debug 設定。 *Web.config*檔案必須正確設定，才能進行偵錯工具。 先前章節中的**屬性**設定會更新*web.config*檔案，但您也可以手動進行設定。

> [!NOTE]
> ASP.NET Core 專案一開始不會有*web.config*檔案，但會使用*appsettings*和*launchsettings.json*檔案來進行應用程式設定和啟動資訊。 部署應用程式會在專案中建立*web.config*檔案或檔案，但它們通常不會包含 debug 資訊。

> [!TIP]
> 您的部署程式可能會更新*web.config*設定，因此在嘗試進行 debug 之前，請確定*web.config*已設定為可進行偵錯工具。

**若要手動設定*web.config*檔案以進行偵錯工具：**

1. 在 Visual Studio 中，開啟 ASP.NET 專案的*web.config*檔案。

2. *Web.config 是一個*XML 檔案，因此包含以標記標記的嵌套區段。 找出 `configuration/system.web/compilation` 區段。 （如果 `compilation` 元素不存在，請加以建立）。

3. 請確定 `compilation` 元素中的 `debug` 屬性已設定為 [`true`]。 （如果 `compilation` 專案未包含 `debug` 屬性，請將它加入，並將它設定為 `true`）。

   如果您使用本機 IIS，而不是預設的 IIS Express server，請確定 `compilation` 元素中的 `targetFramework` 屬性值符合 IIS 伺服器上的架構。

   *Web.config 檔案*的 `compilation` 元素看起來應該如下列範例所示：

   > [!NOTE]
   > 這個範例是部分的*web.config*檔案。 `configuration` 和 `system.web` 元素中通常會有額外的 XML 區段，而 `compilation` 元素也可能包含其他屬性和元素。

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 會自動偵測任何 *Web.config* 檔案變更，並套用新的組態設定。 您不需要重新開機電腦或 IIS 伺服器，變更就會生效。

網站可以包含數個虛擬目錄和子目錄，其中每個都有*web.config*檔案。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式會從 URL 路徑中較高層級*的 web.config 檔案*繼承設定設定。 階層式*web.config*檔案設定會套用至階層中底下的所有 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式。 在階層中較低層*的 web.config 檔案*中設定不同的設定，會覆寫較高檔案中的設定。

例如，如果您在<em>www.microsoft.com/aaa/web.config</em>中指定 `debug="true"`， *aaa*資料夾或*aaa*之任何子資料夾中的任何應用程式都會繼承該設定，除非其中一個應用程式以自己的 web.config 覆寫此設定 *。* 文字檔.

## <a name="publish-in-debug-mode-using-the-file-system"></a>使用檔案系統在 debug 模式中發佈

有不同的方式可將應用程式發佈至 IIS。 下列步驟示範如何使用檔案系統來建立和部署 debug 發行設定檔。 若要這樣做，您必須以系統管理員身分執行 Visual Studio。

> [!IMPORTANT]
> 如果您變更程式碼或重建，您必須重複這些步驟以重新發佈。

1. 在 Visual Studio 中，以滑鼠右鍵按一下專案，然後選擇 [**發佈**]。

3. 選擇 [ **IIS]、[FTP] 等**，然後按一下 [**發佈**]。

    ![發行至 IIS](media/dbg-aspnet-local-iis.png "發佈至 IIS")

4. 在 [ **CustomProfile** ] 對話方塊中，針對 [**發行方法**] 選擇 [**檔案系統**]。

5. 針對 [**目標位置**]，選取 **[流覽**（ **...** ）]。

   - 針對 [ASP.NET]，選取 [**本機 IIS**]，選取您為應用程式建立的網站，然後選取 [**開啟**]。

     ![發佈至 IIS 的 ASP.NET](media/dbg-aspnet-local-iis1.png "將 ASP.NET 發行至 IIS")

   - 在 [ASP.NET Core] 中，選取 [**檔案系統**]，選取您為應用程式設定的資料夾，然後選取 [**開啟**]。

1. 選取 [下一步]。

1. 在 [設定] 下，從下拉式**清單中選取**[ **Debug** ]。

1. 選取 [儲存]。

1. 在 [**發佈**] 對話方塊中，確定 [ **CustomProfile** ] （或您剛建立的設定檔名稱）出現，並將 [ **LastUsedBuildConfiguration** ] 設定為 [ **Debug**]。

1. 選取 [發行]。

    ![發行至 IIS](media/dbg-aspnet-local-iis-select-site.png "發佈至 IIS")

> [!IMPORTANT]
> Debug 模式可大幅降低應用程式的效能。 為了達到最佳效能，請在*web.config*中設定 `debug="false"`，並在部署生產應用程式或執行效能測量時指定發行組建。

## <a name="see-also"></a>請參閱
- [ASP.NET 偵錯：系統需求](aspnet-debugging-system-requirements.md)
- [如何：在使用者帳戶下執行背景工作處理序](how-to-run-the-worker-process-under-a-user-account.md)
- [如何：尋找 ASP.NET 處理序的名稱](how-to-find-the-name-of-the-aspnet-process.md)
- [Debug deployed web applications](debugging-deployed-web-applications.md) (對已部署的 Web 應用程式進行偵錯)
- [Walkthrough: Debugging a web form](walkthrough-debugging-a-web-form.md) (逐步解說：對 Web 表單進行偵錯)
- [如何：對 ASP.NET 例外狀況進行偵錯](how-to-debug-aspnet-exceptions.md)
- [Debug web applications: Errors and troubleshooting](debugging-web-applications-errors-and-troubleshooting.md) (對 Web 應用程式進行偵錯：錯誤和疑難排解)
