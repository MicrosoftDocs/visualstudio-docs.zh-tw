---
title: 使用 IntelliTrace 獨立收集器 |Microsoft Docs
description: 您可以使用 IntelliTrace 獨立收集器來收集資料，而不需要安裝 Visual Studio 而不需要變更目標系統的環境。
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 251b15edc838a1231e017d8f23b04f8bbb773692
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840869"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>使用 IntelliTrace 獨立收集器 (c #、Visual Basic) 

**IntelliTrace 獨立收集器** 可讓您收集生產伺服器或其他環境上 App 的 IntelliTrace 診斷資料，而不需要在目標電腦上安裝 Visual Studio，而且不需要變更目標系統的環境。 IntelliTrace 獨立收集器適用於 Web、Sharepoint、WPF 和 Windows Forms App。 完成資料收集時，只要刪除收集器，就可以將其解除安裝。

 觀看 IntelliTrace 實際操作： [收集和分析生產環境中的 IntelliTrace 資料以進行偵錯 (Channel 9 影片)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> 您也可以透過 **Trace** 模式使用 **Microsoft Monitoring Agent** ，即可收集遠端電腦上執行之 Web 和 Sharepoint App 的相同 IntelliTrace 資料。
>
> 您可以透過 **Monitor** 模式執行代理程式，即可在 IntelliTrace 資料中收集效能相關事件。 **Monitor** 模式的效能影響低於 **Trace** 模式或 **IntelliTrace 獨立收集器**。 Microsoft Monitoring Agent 在安裝時確實會變更目標系統的環境。 請參閱 [使用 Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md)。
> IntelliTrace 獨立收集器不支援處理快照集。

 **需求**

- .NET Framework 3.5 或更高版本

- 在開發電腦或其他要開啟 .iTrace 檔案的電腦上已安裝 Visual Studio Enterprise (但不能是 Professional 或 Community 版本)

  > [!NOTE]
  > 請務必儲存符號 (.pdb) 檔案。 若要使用 IntelliTrace 進行偵錯並逐步執行程式碼，您必須具有相符的原始程式檔和符號檔。 請參閱 [在部署後診斷問題](../debugger/diagnose-problems-after-deployment.md)。

  **常見問題集**

- [哪些 App 與收集器搭配使用？](#WhatApps)

- [如何開始？](#GetStarted)

- [如何取得大部分的資料，而不會讓 App 變慢？](#Minimizing)

- [我還可以在哪裏取得 IntelliTrace 資料？](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> 哪些應用程式可與收集器搭配使用？

- ASP.NET Internet Information Services (IIS 上裝載的 Web 應用程式) 7.0、7.5、8.0、12.0 和16.0 版

- SharePoint 2010 和 SharePoint 2013 應用程式

- Windows Presentation Foundation (WPF) 和 Windows Forms App。

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> 如何? 開始使用嗎？

1. [安裝收集器](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [設定收集器目錄的權限](#ConfigurePermissionsRunningCollector)

3. [安裝 IntelliTrace PowerShell Cmdlet 以收集 Web App 或 SharePoint 應用程式的資料](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [設定 .iTrace 檔案目錄的權限](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [從 Web App 或 SharePoint 應用程式收集資料](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -或-

     [從 Managed App 收集資料](#BKMK_Collect_Data_from_Executables)

6. [在 Visual Studio Enterprise 中，開啟 .iTrace 檔案。](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> 安裝收集器

1. 在 App 伺服器上，建立收集器目錄，例如：**C:\IntelliTraceCollector**

2. 從 [Microsoft 下載中心](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019)、 [My.visualstudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)或 Visual Studio 2013 Update 3 安裝資料夾取得收集器。 [IntelliTrace Collector for Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909)::

   - **Microsoft 下載中心** 或 **my.visualstudio.com**：

     1. 選擇 **IntelliTraceCollector.exe** 旁邊的 [下載] 。

     2. 將 IntelliTraceCollector.exe 儲存至收集器目錄，例如： **C:\IntelliTraceCollector**

     3. 執行 IntelliTraceCollector.exe。 這會解壓縮 IntelliTraceCollection.cab 檔案。

        \- 或 -

   - **Visual Studio 安裝資料夾**：

     1. 從安裝收集器的資料夾複製 IntelliTraceCollection.cab，例如：

          **..\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          或者，針對舊版 Visual Studio：

          **..\Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. 將 IntelliTraceCollection.cab 放入收集器目錄，例如： **C:\IntelliTraceCollector**

3. 展開 IntelliTraceCollection.cab：

   1. 在 App 伺服器上，以系統管理員身分開啟命令提示字元視窗。

   2. 瀏覽至收集器目錄，例如： **C:\IntelliTraceCollector**

   3. 使用 **expand** 命令 (結尾含句點 (**.**))，以展開 IntelliTraceCollection.cab：

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > 句點 (**.**) 會保留含有當地語系化收集計劃的子資料夾。

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> 設定收集器目錄的許可權

1. 在 App 伺服器上，以系統管理員身分開啟命令提示字元視窗。

2. 使用 Windows **icacls** 命令，授與伺服器管理員收集器目錄的完整權限。 例如：

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. 收集 Web App 或 SharePoint 應用程式的資料：

    1. 將收集器目錄的完整權限授與執行 IntelliTrace PowerShell Cmdlet 的人員。

         例如：

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. 將收集器目錄的讀取和執行權限授與 Web App 或 SharePoint 應用程式的應用程式集區。

         例如：

        - 針對 **DefaultAppPool** 應用程式集區中的 Web 應用程式：

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - 針對 **SharePoint - 80** 應用程式集區中的 SharePoint 應用程式：

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> 安裝 IntelliTrace PowerShell Cmdlet 以收集 Web 應用程式或 SharePoint 應用程式的資料

1. 在 App 伺服器上，確認已啟用 PowerShell。 在大部分的 Windows Server 版本上，您可以在 [伺服器管理員]  系統管理工具中加入這項功能。

     ![使用 [伺服器管理員] 新增 PowerShell](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. 安裝 IntelliTrace PowerShell Cmdlet。

    1. 以系統管理員身分開啟 PowerShell 命令提示字元視窗。

        1. 依序選擇 [開始] 、[所有程式] 、[附屬應用程式] 和 [Windows PowerShell] 。

        2. 選擇下列其中一個步驟：

            - 在 64 位元作業系統上，開啟 **Windows PowerShell** 的捷徑功能表。 選擇 [以系統管理員身分執行] 。

            - 在 32 位元作業系統上，開啟 **Windows PowerShell (x86)** 的捷徑功能表。 選擇 [以系統管理員身分執行] 。

    2. 在 PowerShell 命令視窗中，使用 **Import-Module** 命令匯入 **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**。

         例如：

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> 設定 .Itrace 檔案目錄的許可權

1. 在 App 伺服器上，建立 .iTrace 檔案目錄，例如：**C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - 若要避免讓應用程式變慢，請選擇本機高速磁碟上不是非常活躍的位置。
   >   - 您可以將 .iTrace 檔案和收集器檔案放在相同的位置。 不過，如果您有 Web App 或 SharePoint 應用程式，請確認這個位置是在裝載應用程式的目錄外部。
   >
   > [!IMPORTANT]
   > - 限制 iTrace 檔案目錄，僅供必須使用收集器的識別使用。 .ITrace 檔案可能包含機密資訊 (例如使用者、資料庫、其他來源位置和連接字串中的資料)，因為 IntelliTrace 可以記錄傳遞給方法參數或做為傳回值的任何資料。
   >   - 請確定可以開啟 .iTrace 檔案的人具有檢視機密資料的授權。 共用 .iTrace 檔案時請小心。 如果其他人必須具有存取權，請將檔案複製到安全的共用位置。

2. 針對 Web App 或 SharePoint 應用程式，將 .iTrace 檔案目錄的完整權限授與其應用程式集區。 您可以使用 Windows **icacls** 命令，或使用 Windows 檔案總管 (或檔案總管)。

    例如：

   - 使用 Windows **icacls** 命令設定權限：

     - 針對 **DefaultAppPool** 應用程式集區中的 Web 應用程式：

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - 針對 **SharePoint - 80** 應用程式集區中的 SharePoint 應用程式：

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -或-

   - 使用 Windows 檔案總管 (或檔案總管) 設定權限：

     1. 開啟 .iTrace 檔案目錄的 [屬性]  。

     2. 在 [安全性]  索引標籤上，依序選擇 [編輯] 和 [新增] 。

     3. 請確認 [內建安全性主體]  出現在 [選取這個物件類型]  方塊中。 如果未出現，請選擇 [物件類型]，以將它加入。

     4. 請確認您的本機電腦出現在 [從這個位置]  方塊中。 如果未出現，請選擇 [位置] 變更它。

     5. 在 [ **輸入物件名稱來選取** ] 方塊中，加入 Web 應用程式或 SharePoint 應用程式的應用程式集區。

     6. 選擇 [檢查名稱]  來解析名稱。 選擇 [確定]。

     7. 請確認應用程式集區具有 [完全控制] 。

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> 從 Web 應用程式或 SharePoint 應用程式收集資料

1. 若要開始收集資料，請以系統管理員身分開啟 PowerShell 命令視窗，然後執行此命令：

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > 執行這個命令之後，請輸入 **Y** ，確認您想要開始收集資料。

     例如，從 **SharePoint - 80** 應用程式集區的 SharePoint 應用程式中收集資料：

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |名稱|描述|
    |-|-|
    |*ApplicationPool*|在其中執行應用程式的應用程式集區名稱|
    |*收集計劃的路徑*|收集計劃 (可進行收集器設定的 .xml 檔案) 的路徑。<br /><br /> 您可以指定收集器所隨附的計劃。 下列計劃適用於 Web App 和 SharePoint 應用程式：<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     僅收集 IntelliTrace 事件和 SharePoint 事件 (包括例外狀況、資料庫呼叫和 Web 伺服器要求)。<br />-   collection_plan.ASP.NET.trace.xml<br />     收集函式呼叫和 collection_plan.ASP.NET.default.xml 中的所有資料。 這個計劃適用於進行詳細分析，但可能會讓 App 變得比 collection_plan.ASP.NET.default.xml 更慢。<br /><br /> 若要避免讓 App 變慢，請自訂這些計劃，或建立自己的計劃。 基於安全考量，請將任何自訂計劃與收集器檔案放在相同的安全位置。 請參閱 [建立和自訂 IntelliTrace 收集計劃](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) 和 [如何取得大部分的資料，而不會讓 App 變慢？](#Minimizing) **注意：**  根據預設，.Itrace 檔案的大小上限為 100 MB。 .iTrace 檔案達到這個限制時，收集器會刪除檔案的最早項目，以挪出空間供較新的項目使用。 若要變更此限制，請編輯收集計劃的 `MaximumLogFileSize` 屬性。 <br /><br /> *我可以在哪裡找到這些收集計劃的當地語系化版本？*<br /><br /> 您可以在收集器的子資料夾中找到當地語系化計劃。|
    |*iTrace 檔案目錄的完整路徑*|.iTrace 檔案目錄的完整路徑。 **安全性注意事項：**  提供完整路徑，而非相對路徑。|

     收集器會附加至應用程式集區，並開始收集資料。

     *「我現在可以開啟 .iTrace 檔案嗎？」* (Can I open the .iTrace file at this time?)不可以，在資料收集期間會鎖定檔案。

2. 重現問題。

3. 若要建立 .Itrace 檔案的檢查點，請使用下列語法：

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. 若要檢查收集狀態，請使用此語法：

     `Get-IntelliTraceCollectionStatus`

5. 若要停止收集資料，請使用此語法：

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > 執行這個命令之後，請輸入 **Y** ，確認您想要停止收集資料。 否則，收集器可能會繼續收集資料、.iTrace 檔案會保留鎖定，或檔案可能未包含任何有用的資料。

6. [在 Visual Studio Enterprise 中，開啟 .iTrace 檔案。](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> 從受控應用程式收集資料

1. 若要同時啟動 App 並收集資料，請使用此語法：

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     例如，從名稱為 **MyApp** 的 App 收集資料：

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |名稱|描述|
    |-|-|
    |*收集器可執行檔 IntelliTrace 的完整路徑*|收集器可執行檔 IntelliTraceSC.exe 的完整路徑|
    |*收集計劃的路徑*|收集計劃 (可進行收集器設定的 .xml 檔案) 的路徑。<br /><br /> 您可以指定收集器所隨附的計劃。 下列計劃適用於 Managed App：<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     僅收集 IntelliTrace 事件，包括例外狀況、資料庫呼叫和 Web 伺服器要求。<br />-   collection_plan.ASP.NET.trace.xml<br />     收集函式呼叫和 collection_plan.ASP.NET.default.xml 中的所有資料。 這個計劃適用於進行詳細分析，但可能會讓 App 變得比 collection_plan.ASP.NET.default.xml 更慢。<br /><br /> 若要避免讓 App 變慢，請自訂這些計劃，或建立自己的計劃。 基於安全考量，請將任何自訂計劃與收集器檔案放在相同的安全位置。 請參閱 [建立和自訂 IntelliTrace 收集計劃](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) 和 [如何取得大部分的資料，而不會讓 App 變慢？](#Minimizing) **注意：**  根據預設，.Itrace 檔案的大小上限為 100 MB。 .iTrace 檔案達到這個限制時，收集器會刪除檔案的最早項目，以挪出空間供較新的項目使用。 若要變更此限制，請編輯收集計劃的 `MaximumLogFileSize` 屬性。 <br /><br /> *我可以在哪裡找到這些收集計劃的當地語系化版本？*<br /><br /> 您可以在收集器的子資料夾中找到當地語系化計劃。|
    |*.iTrace 檔案目錄及檔案名稱的完整路徑*|.iTrace 檔案目錄以及副檔名為 **.itrace** 之 .iTrace 檔案名稱的完整路徑。 **安全性注意事項：**  提供完整路徑，而非相對路徑。|
    |*應用程式可執行檔案及檔案名稱的完整路徑*|Managed App 的路徑和檔案名稱|

2. 結束 App，以停止資料收集。

3. [在 Visual Studio Enterprise 中，開啟 .iTrace 檔案。](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a> 在 Visual Studio Enterprise 中開啟 .Itrace 檔案

> [!NOTE]
> 若要使用 IntelliTrace 進行偵錯並逐步執行程式碼，您必須具有相符的原始程式檔和符號檔。 請參閱 [在部署後診斷問題](../debugger/diagnose-problems-after-deployment.md)。

1. 移動此 .iTrace 檔案，或將它複製到具有 Visual Studio Enterprise (但不是 Professional 或 Community 版本) 的電腦。

2. 在 Visual Studio 外部按兩下 .iTrace 檔案，或從 Visual Studio 內開啟該檔案。

     Visual Studio 會顯示 [IntelliTrace 摘要]  頁面。 在大部分的區段中，您都可以檢閱事件或其他項目，並選擇一個項目，然後在發生事件的位置以及時間使用 IntelliTrace 開始偵錯。 請參閱 [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)。

    > [!NOTE]
    > 若要使用 IntelliTrace 進行偵錯並逐步執行程式碼，您必須在開發電腦上具有相符的原始程式檔和符號檔。 請參閱 [在部署後診斷問題](../debugger/diagnose-problems-after-deployment.md)。

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> 如何? 取得大部分的資料，而不會讓應用程式變慢嗎？
 IntelliTrace 可以收集大量資料，因此對您 App 效能的影響取決於 IntelliTrace 所收集的資料以及所分析的程式碼種類。 請參閱 [最佳化實際伺服器上的 IntelliTrace 收集](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)。

 以下是一些取得大部分資料而不會讓 App 變慢的方法：

- 只有在您認為有問題或是可以重現問題時，才執行收集器。

   開始收集，並重現問題，然後停止收集。 在 Visual Studio Enterprise 中開啟 .iTrace 檔案，並檢查資料。 請參閱 [在 Visual Studio Enterprise 中，開啟 .iTrace 檔案](#BKMK_View_IntelliTrace_Log_Files)。

- 針對 Web App 和 SharePoint 應用程式，收集器會為每個共用指定應用程式集區的應用程式記錄資料。 這可能會讓任何共用相同應用程式集區的 App 變慢，即使您只能在收集計劃中指定單一 App 的模組也是一樣。

   若要防止收集器讓其他 App 變慢，請在它自己的應用程式集區中裝載每個 App。

- 檢閱 IntelliTrace 在收集計劃中為其收集資料的事件。 編輯收集計劃，以停用不相關或您不感興趣的事件。

   若要停用事件，請將 `enabled` 項目的 `<DiagnosticEventSpecification>` 屬性設為 `false`：

   `<DiagnosticEventSpecification enabled="false">`

   如果 `enabled` 屬性不存在，表示已啟用事件。

   *這樣如何改善效能？*

  - 您可以停用與 App 無關的事件，以減少啟動時間。 例如，針對未使用 Windows Workflow 的 App 停用 Windows Workflow 事件。

  - 您可以針對存取登錄但未顯示登錄設定問題的應用程式停用登錄事件，以改善啟動和執行時間效能。

- 檢閱 IntelliTrace 在收集計劃中為其收集資料的模組。 編輯收集計劃，使其只包括您感興趣的模組：

  1. 開啟收集計劃。 尋找 `<ModuleList>` 元素。

  2. 在 `<ModuleList>`中，將 `isExclusionList` 屬性設為 `false`。

  3. 使用 `<Name>` 項目，即可指定每個具有下列其中一個項目的模組：檔案名稱、包括其名稱中含有該字串之任何模組的字串值，或公開金鑰。

     例如，若只要收集 Fabrikam Fiber Web App 之主要 Web 模組中的資料，請建立與下面類似的清單：

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>
  ```

   若要從任何名稱中包括 "Fabrikam" 的模組中收集資料，請建立與下面類似的清單：

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>
  ```

   若要透過指定模組的公開金鑰語彙基元，以從模組中收集資料，請建立與下面類似的清單：

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>
  ```

   *這樣如何改善效能？*

   這樣會減少 IntelliTrace 在啟動和執行 App 時所收集的方法呼叫資訊量與其他檢測資料量。 這項資料可讓您：

  - 在收集資料之後逐步執行程式碼。

  - 檢查傳遞給函式呼叫的值以及從函式呼叫傳回的值。

    *為何不改為排除模組？*

    根據預設，收集計劃會透過將 `isExclusionList` 屬性設為 `true`來排除模組。 不過，排除模組時收集到的資料，還是可能來自不符合清單準則的模組，以及您可能不感興趣的模組，例如協力廠商或開放原始碼模組。

- *是否有任何 IntelliTrace 不會收集的資料？*

   是，為了降低對效能的影響，IntelliTrace 會限制只對下列值進行資料收集：傳遞給方法以及從方法傳回的基本資料類型值，以及傳遞給方法以及從方法傳回之最上層物件欄位中的基本資料類型值。

   例如，假設您有接受整數 `AlterEmployee` 和 `id` 物件 `Employee` 的 `oldemployee`方法簽章：

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee` 類型具有下列屬性： `Id`、 `Name`和 `HomeAddress`。 `Employee` 與 `Address` 類型之間具有關聯。

   ![Employee 和 Address 之間的關聯性](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   收集器會記錄 `id`方法所傳回 `Employee.Id`、 `Employee.Name` 、 `Employee` 和 `AlterEmployee` 物件的值。 不過，收集器不會記錄 `Address` 物件的資訊，不論此物件是否為 Null。 收集器也不會記錄 `AlterEmployee` 方法中區域變數的資料，除非其他方法使用這些區域變數做為參數 (當時記錄為方法參數)。

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> 我還可以在哪裡取得 IntelliTrace 資料？

您可以從 Visual Studio Enterprise 中的 IntelliTrace 偵錯工具取得 IntelliTrace 資料。 請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。

## <a name="where-can-i-get-more-information"></a>我可以在哪裡取得詳細資訊？
 [使用儲存的 IntelliTrace 資料](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>部落格
 [遠端使用 IntelliTrace 獨立收集器](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [建立和自訂 IntelliTrace 收集計劃](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [最佳化實際伺服器上的 IntelliTrace 收集](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>論壇
 [Visual Studio 偵錯工具](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>影片
 [Channel 9 影片：收集和分析生產環境中的資料](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
