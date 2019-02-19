---
title: 從命令列加入階層互動資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c591af9259a4a45af762e79552c99671a094d0f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778879"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>從命令列加入階層互動資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在與一或多個資料庫通訊的多階層應用程式函式中，階層互動分析提供會同步 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 呼叫執行時間的額外資訊。  
  
 **Windows 8 和 Windows Server 2012**  
  
 若要在 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式上收集階層互動資料，您必須使用檢測方法。 不支援收集 Windows 市集應用程式上的階層互動資料。  
  
 **Visual Studio 版本**  
  
 使用 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 或 [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] 可以收集階層互動分析。 不過，只能在 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 和 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 中檢視階層互動分析資料。  
  
 **在遠端電腦上收集 TIP 資料**  
  
 若要在遠端電腦上收集階層互動資料，您必須從 Visual Studio 電腦的 _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** 資料夾中，將 **vs\_profiler\_**_\<平台>_**\_**_\<語言>_**.exe** 檔案複製到遠端電腦並加以安裝。 您無法使用 [Visual Studio 遠端工具](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 下載封裝的程式碼剖析工具。  
  
 **TIP 報告**  
  
 階層互動資料只能在 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] IDE 中檢視。 不提供透過 [VSPerfReport](../profiling/vsperfreport.md) 的檔案型階層互動報告。  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>使用 VSPerfCmd 加入階層互動資料  
 VSPerfASPNETCmd 命令列工具可讓您存取程式碼剖析工具中的完整功能。 若要使用 VSPerfCmd 將階層互動加入收集的分析資料，您必須使用 **VSPerfCLREnv** 公用程式來設定和移除啟用階層互動資料的環境變數。 您指定的選項和收集資料所需的程序，取決於您正在分析的應用程式類型。  
  
### <a name="profiling-stand-alone-applications"></a>對獨立應用程式進行程式碼剖析  
 若要將階層互動資料加入未由另一個處理程序執行的應用程式，例如對 SQLServer 資料庫進行同步 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 呼叫的 Windows 傳統型應用程式，請使用 **VSPerfClrEnv /InteractionOn** 選項設定環境變數，並使用 **VSPerfClrEnv /InteractionOff** 選項將它們移除。  
  
 下列範例中會使用檢測方法對 Windows 桌面應用程式進行程式碼剖析，並且收集階層互動資料。  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>對 Windows 傳統型應用程式進行程式碼剖析的範例  
  
1. 使用系統管理員權限開啟命令提示視窗。 按一下 [開始]，然後依序指向 [所有程式] 和 [附屬應用程式]。 用右鍵按一下 [命令提示字元]，然後按一下 [以系統管理員身份執行]。  
  
2. 初始化 .NET 程式碼剖析和 TIP 環境變數。 輸入下列命令：  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. 啟動分析工具。 輸入下列命令：  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. 使用 VSPerfCmd 啟動應用程式。 輸入下列命令：  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. 執行應用程式以收集分析資料，接著按照一般方式關閉應用程式。  
  
6. 清除 TIP 環境變數。 輸入下列命令：  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   如需詳細資訊，請參閱[對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)。  
  
### <a name="profiling-services"></a>對服務進行程式碼剖析  
 若要分析服務 (包括 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 應用程式)，請使用 **VSPerfClrEnv /GlobalInteractionOn** 選項設定環境變數，再使用 **VSPerfClrEnv /GlobalInteractionOff** 選項將它們移除。  
  
 當您分析服務 (包括[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式時)，您通常需要重新啟動電腦以啟用程式碼剖析。  
  
 下列範例中會使用檢測方法對 Windows 服務進行程式碼剖析，並且收集階層互動資料。  
  
##### <a name="profiling-a-windows-service-example"></a>對 Windows 服務進行程式碼剖析的範例  
  
1. 如有必要，請安裝服務。  
  
2. 使用系統管理員權限開啟命令提示視窗。 按一下 [開始]，然後依序指向 [所有程式] 和 [附屬應用程式]。 用右鍵按一下 [命令提示字元]，然後按一下 [以系統管理員身份執行]。  
  
3. 初始化 .NET 程式碼剖析環境變數。 輸入下列命令：  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. 初始化 TIP 環境變數。 輸入下列命令  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. 重新啟動電腦以註冊環境變數。  
  
6. 使用系統管理員權限開啟命令提示視窗。  
  
7. 啟動分析工具。 輸入下列命令：  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. 如有必要，請啟動服務。  
  
9. 將程式碼剖析工具附加至服務。 輸入下列命令：  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. 執行服務並收集分析資料。  
  
11. 停止程式碼剖析工具。 輸入下列命令：  
  
     `vsperfcmd /detach`  
  
12. 初始化 .NET 和 TIP 程式碼剖析環境變數。 輸入下列命令：  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. 重新啟動電腦以註冊清除的環境變數。  
  
    如需詳細資訊，請參閱下列其中一個主題：  
  
    [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>使用 VSPerfASPNETCmd 加入階層互動資料  
 VSPerfASPNETCmd 命令列工具可讓您輕鬆地分析 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式。 相較於 **VSPerfCmd** 命令列工具，選項變少，無須設定任何環境變數，也不需要重新啟動電腦。 VSPerfASPNETCmd 的這些功能使得階層互動資料的收集變得格外輕鬆。  
  
 若要使用 VSPerfASPNETCmd 將階層互動加入收集的分析資料，請將 **/TIP** 選項加入命令列。 例如，透過檢測方法使用下列命令列收集 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式的階層互動資料：  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 如需 VSPerfASPNETCmd 的詳細資訊，請參閱[使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。
