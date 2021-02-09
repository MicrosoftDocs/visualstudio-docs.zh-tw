---
title: 從命令列加入階層互動資料 | Microsoft Docs
description: 對於與一或多個資料庫通訊的多層式應用程式，請使用階層互動分析來取得同步呼叫的執行時間資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9070e515fd59f7b29427f20322ef6cb1a01afaee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901332"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>從命令列新增階層互動資料

在與一或多個資料庫通訊的多階層應用程式函式中，階層互動分析提供會同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼叫執行時間的額外資訊。

**Windows 8 與 Windows Server 2012**

若要在 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式上收集階層互動資料，您必須使用檢測方法。 不支援收集 UWP 應用程式上的階層互動資料。

**Visual Studio 版本**

階層互動分析可以使用任何版本的 Visual Studio 來收集。 不過，階層互動分析資料只能在 Visual Studio Enterprise 中檢視。

**在遠端電腦上收集 TIP 資料**

若要在遠端電腦上收集階層互動資料， **\_** 您必須 _\<Platform>_ **\_** _\<Language>_ 從 Visual Studio 機的 _% VSInstallDir%_**\Team Tools\Performance Tools\Setups** 資料夾中，將 vs_profiler **.exe** 檔案複製到遠端電腦，並加以安裝。 您無法使用[遠端偵錯](../debugger/remote-debugging.md)下載套件中的程式碼剖析工具。

**TIP 報告**

階層互動資料只能在 Visual Studio Enterprise 中檢視。 不提供透過 [VSPerfReport](../profiling/vsperfreport.md) 的檔案型階層互動報告。

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>使用 VSPerfCmd 加入階層互動資料

VSPerfASPNETCmd 命令列工具可讓您存取程式碼剖析工具中的完整功能。 若要使用 VSPerfCmd 將階層互動加入收集的分析資料，您必須使用 **VSPerfCLREnv** 公用程式來設定和移除啟用階層互動資料的環境變數。 您指定的選項和收集資料所需的程序，取決於您正在分析的應用程式類型。

## <a name="profile-stand-alone-applications"></a>分析獨立應用程式

若要將階層互動資料加入未由另一個處理程序執行的應用程式，例如對 SQLServer 資料庫進行同步 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 呼叫的 Windows 傳統型應用程式，請使用 **VSPerfClrEnv /InteractionOn** 選項設定環境變數，並使用 **VSPerfClrEnv /InteractionOff** 選項將它們移除。

下列範例中會使用檢測方法對 Windows 桌面應用程式進行程式碼剖析，並且收集階層互動資料。

### <a name="profile-a-windows-desktop-application-example"></a>對 Windows 傳統型應用程式進行分析的範例

1. 使用系統管理員權限開啟命令提示視窗。 按一下 [開始]，然後依序指向 [所有程式] 和 [附屬應用程式]。 以滑鼠右鍵按一下 [ **命令提示** 字元]，然後按一下 [以 **系統管理員身分執行**]。

2. 初始化 .NET 程式碼剖析和 TIP 環境變數。 輸入下列命令：

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. 啟動分析工具。 輸入以下命令：

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. 使用 VSPerfCmd 啟動應用程式。 輸入以下命令：

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. 執行應用程式以收集分析資料，接著按照一般方式關閉應用程式。

6. 清除 TIP 環境變數。 輸入以下命令：

    ```cmd
    vsperfclrenv /off
    ```

如需詳細資訊，請參閱[分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)。

## <a name="profile-services"></a>分析服務

若要分析服務 (包括 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式)，請使用 **VSPerfClrEnv /GlobalInteractionOn** 選項設定環境變數，再使用 **VSPerfClrEnv /GlobalInteractionOff** 選項將它們移除。

當您分析服務 (包括[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式時)，您通常需要重新啟動電腦以啟用程式碼剖析。

下列範例中會使用檢測方法對 Windows 服務進行分析，並且收集階層互動資料。

### <a name="profile-a-windows-service-example"></a>對 Windows 服務進行分析的範例

1. 如有必要，請安裝服務。

2. 使用系統管理員權限開啟命令提示視窗。 按一下 [開始]，然後依序指向 [所有程式] 和 [附屬應用程式]。 以滑鼠右鍵按一下 [ **命令提示** 字元]，然後按一下 [以 **系統管理員身分執行**]。

3. 初始化 .NET 程式碼剖析環境變數。 輸入以下命令：

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. 初始化 TIP 環境變數。 輸入以下命令：

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. 重新啟動電腦以註冊環境變數。

6. 使用系統管理員權限開啟命令提示視窗。

7. 啟動分析工具。 輸入以下命令：

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. 如有必要，請啟動該服務。

9. 將程式碼剖析工具附加至服務。 輸入以下命令：

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. 執行服務並收集分析資料。

11. 停止程式碼剖析工具。 輸入以下命令：

     `vsperfcmd /detach`

12. 初始化 .NET 和 TIP 程式碼剖析環境變數。 輸入以下命令：

    ```cmd
    vsperfclrenv /globaloff
    ```

13. 重新啟動電腦以註冊清除的環境變數。

如需詳細資訊，請參閱下列其中一個主題：

[分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[分析服務](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>使用 VSPerfASPNETCmd 加入階層互動資料

VSPerfASPNETCmd 命令列工具可讓您輕鬆地分析 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。 相較於 **VSPerfCmd** 命令列工具，選項變少，無須設定任何環境變數，也不需要重新啟動電腦。 VSPerfASPNETCmd 的這些功能使得階層互動資料的收集變得格外輕鬆。

若要使用 VSPerfASPNETCmd 將階層互動加入收集的分析資料，請將 **/TIP** 選項加入命令列。 例如，透過檢測方法使用下列命令列收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的階層互動資料：

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

如需 VSPerfASPNETCmd 的詳細資訊，請參閱 [使用 VSPerfASPNETCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。
