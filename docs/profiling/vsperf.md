---
title: VSPerf | Microsoft Docs
description: 瞭解如何使用 Vsperf.exe 命令列工具，在裝置上未安裝 Visual Studio 時，從命令列分析 UWP 應用程式。
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 95c82b6c00d3a3b3af2a58232ed0d65df5b5f76f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911633"
---
# <a name="vsperf"></a>VSPerf
使用 **VsPerf** 命令列工具，可以︰

1. 在裝置上未安裝 Visual Studio 時，從命令列來分析 UWP 應用程式。

2. 使用取樣分析方法來分析 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式。

   如需程式碼剖析選項的詳細資訊，請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="uwp-apps-only"></a>僅限 UWP 應用程式
 這些選項僅適用於 UWP 應用程式。

|選項|Description|
|-|-|
|**/app:{AppName}**|從 [開始] 功能表啟動分析工具，並等候指定的應用程式啟動。<br /><br /> 執行 `vsperf /listapps` 來檢視已安裝應用程式的 AppName 和 PackageFullName。|
|**/package:{PackageFullName}**|從 [開始] 功能表啟動分析工具，並等候指定的應用程式啟動。<br /><br /> 執行 `vsperf /listapps` 來檢視已安裝應用程式的 AppName 和 PackageFullName。|
|**/js**|分析 JavaScript 應用程式時的必要項。<br /><br /> 可從 JavaScript 應用程式收集效能資料。<br /><br /> 只能搭配 /package 或 /attach 一起使用。|
|**/noclr**|選擇性。 不會收集 CLR 資料。<br /><br /> 只能搭配 /package 或 /attach 一起使用。<br /><br /> 最佳化，不會解析任何 Managed 符號。|
|**/listapps**|列出已安裝應用程式的 AppName 和 PackageFullNames。|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>僅限 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式
 這些選項無法在 UWP 應用程式上運作。

|選項|Description|
|-|-|
|**/launch:{Executable}**|啟動並開始對指定的可執行檔進行程式碼剖析。|
|**/args:{ExecutableArguments}**|指定要傳遞給 **/launch** 目標的命令列引數。|
|**/console**|在新的命令視窗中執行 **/launch** 目標。|

## <a name="all-applications"></a>所有應用程式
 這些選項適用於任何 Windows 8 或 Windows Server 2012 應用程式。

|選項|Description|
|-|-|
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|從指定的處理序收集資料。<br /><br /> 使用 [工作管理員] 來檢視執行中應用程式的處理序識別碼 (PID) 和處理序名稱。|
|**/file:{ReportName}**|選擇性。 指定輸出檔案 (覆寫現有的檔案)。<br /><br /> 只能搭配 /package 或 /attach 一起使用。|
|**/pause**|暫停資料收集。|
|**/resume**|繼續資料收集。|
|**/stop**|停止資料收集，並終止目標處理序。|
|**/detach**|停止資料收集，但讓目標處理序繼續執行。|
|**/status**|顯示分析工具的狀態。|

## <a name="see-also"></a>另請參閱
- [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)
