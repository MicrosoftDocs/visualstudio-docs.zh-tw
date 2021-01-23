---
title: Windows 8 & WS 2012 應用程式的效能工具
description: 瞭解 Windows 8 和 Windows Server 2012 中的增強式安全性功能，是否需要大幅變更 Visual Studio 效能工具收集資料的方式。
ms.custom: SEO-VS-2020
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce83684b77d4546915cdcf5980e68be0b6c6a125
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719587"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 和 Windows Server 2012 應用程式的效能工具

自 Windows 8 和 Windows Server 2012 開始的增強式安全性功能需要的重大變更，是 Visual Studio 效能工具在這些平台收集資料的方式。 UWP App 也需要新的收集技術。 本主題描述自 Windows 8 和 Windows Server 2012 平台開始的效能工具變更。

> [!NOTE]
> 其他支援的 Windows 版本 (Windows 7、Windows Server 2008 R2) 的效能工具並未變更。

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>從 Visual Studio IDE 收集 UWP App 資料

當您分析以 JavaScript 和 HTML 5 撰寫的 UWP App 時，要收集 JavaScript 程式碼的檢測資料。 當您分析以 Visual C++、Visual C# 或 Visual Basic 撰寫的 UWP App 或元件時，要收集機器碼和 Managed 程式碼的取樣資料。 您可以在本機或遠端電腦上剖析應用程式的程式碼。

分析 UWP App 時，不支援下列分析功能和選項：

- 使用取樣方法剖析 JavaScript 應用程式。
- 使用檢測方法剖析 Managed 程式碼和機器碼。
- 並行分析
- .NET 記憶體分析
- 階層互動分析 (TIP)
- 取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。
- 檢測選項，例如收集效能和視窗計數器資料，或指定其他命令列選項。

如需對 UWP 應用程式進行分析的詳細資訊，請參閱下列主題：

- [在本機電腦上執行 UWP App](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [在遠端電腦上執行 UWP 應用程式](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [初步認識分析工具](profiling-feature-tour.md)
- [JavaScript 記憶體](../profiling/javascript-memory.md)
- [在本機電腦上分析 UWP App 中的 Visual C++、Visual C# 和 Visual Basic 程式碼](/previous-versions/hh696631(v=vs.140))
- [在遠端裝置上分析 UWP App 中的 Visual C++、Visual C# 和 Visual Basic 程式碼](/previous-versions/hh972878(v=vs.140))
- [分析 UWP App 中 Visual C++、Visual C# 和 Visual Basic 程式碼的效能資料](/previous-versions/hh780914(v=vs.140))

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>從 Visual Studio IDE 收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料

Windows 8 尚未變更使用檢測方法進行程式碼剖析。

階層互動分析 (TIP) 不支援使用取樣方法。

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>使用來自 Visual Studio IDE 的取樣，收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料

使用取樣方法剖析 Windows 8 桌面應用程式或 Windows Server 2012 應用程式時，不支援這些程式碼剖析功能和選項：

- 階層互動分析 (TIP)。 使用檢測支援收集 TIP 資料。

- 取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。

## <a name="profile-from-the-command-line"></a>從命令列分析

您使用兩種命令列工具在 Windows 8 和 Windows Server 2012 的裝置上收集程式碼剖析資料，包括沒有安裝 Visual Studio 的裝置：

|工具名稱|描述|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|從 UWP App 收集分析資料，以及從 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式收集樣本分析資料。|
|[VSPerfCmd](../profiling/vsperfcmd.md)|從 Windows 8 桌面程式或 Windows Server 2012 中執行的應用程式，收集檢測、並行和階層互動分析資料。 從舊版 Windows 中收集所有類型的程式碼剖析資料。|

兩種工具都以 Visual Studio 安裝，以在本機電腦上使用。

若要在沒有安裝 Visual Studio 的裝置上剖析應用程式，請執行下列任一作業：

- 從 [MSDN 網站](https://visualstudio.microsoft.com/#downloads+d-additional-software)下載工具當做 Visual studio 遠端工具的一部分。

- 從您的 Visual Studio 電腦複製並執行獨立的分析工具安裝程式。 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 選擇遠端電腦的作業系統 (x86/x64) 安裝程式。

> [!NOTE]
> 若要收集 TIP 程式碼剖析資料，您必須從遠端電腦的 Visual Studio 電腦安裝獨立分析工具。

從命令列剖析 Windows 8 和 Windows Server 2012 應用程式時，不支援這些程式碼剖析功能和選項：

- 使用取樣模式和 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)，從 Windows 8 和 Windows Server 2012 Web 應用程式收集資料。

- 使用 VsPerfCmd.exe 收集取樣資料。

- 取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。

## <a name="collect-tier-interaction-tip-data"></a>收集階層互動 (TIP) 資料

階層互動分析提供透過 ADO.NET 服務與資料庫通訊之多介層應用程式函式執行時間的其他資訊。 只針對同步函式呼叫收集資料。

**Visual Studio 版本**

階層互動分析資料可以使用任何版本的 Visual Studio 來收集。 不過，階層互動分析資料只能在 Visual Studio Enterprise 中檢視。

**Windows 8 與 Windows Server 2012**

1. 若要從 Windows 8 桌面程式或 Windows Server 2012 中執行的應用程式收集階層互動資料，您必須使用檢測方法。

2. 您無法收集 UWP App 的階層互動資料。

3. 其他支援的 Windows 版本上的所有程式碼剖析方法都可以包含階層互動資料。

**[效能精靈] 和 [效能總管]**

您必須將階層互動資料收集選項加入從 [效能總管] 執行的程式碼剖析。 您也必須將專案、可執行檔或網站加入 [效能總管] 的 [目標] 節點。 請參閱 [收集階層互動資料](../profiling/collecting-tier-interaction-data.md)。

**在遠端電腦上收集 TIP 資料**

若要在遠端電腦上收集階層互動資料，您必須將 **\_ \_** _\<Platform>_ **\_** _\<Language>_ Visual Studio 電腦的 *%VSInstallDir%\Team Tools\Performance Tools\Setups* 資料夾中的 vs profiler **.exe** 檔案複製到遠端電腦，並加以安裝。 您無法使用[遠端偵錯](../debugger/remote-debugging.md)下載套件中的程式碼剖析工具。

您可以使用 [VSPerfCmd](../profiling/vsperfcmd.md) 或 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 收集程式碼剖析資料。

**TIP 報告**

階層互動資料只能在 Visual Studio Enterprise 中檢視。 不提供透過 [VSPerfReport](../profiling/vsperfreport.md) 的檔案型階層互動報告。

## <a name="see-also"></a>另請參閱

[效能總管](../profiling/performance-explorer.md) 
[設定效能會話](../profiling/configuring-performance-sessions.md) 
[從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)