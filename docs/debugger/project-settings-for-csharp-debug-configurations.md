---
title: 'C # debug config 的專案設定 |Microsoft Docs'
description: '瞭解如何使用專案屬性頁的 [偵錯工具] 索引標籤和 [組建] 索引標籤，在 Visual Studio 中變更 c # debug 設定的專案設定。'
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 1adc574241ba34f8170f1c8b1f38c198e3b6ff58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842691"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 偵錯組態的專案設定

您可以在專案屬性頁的 [ [偵錯工具]](#debug-tab) 索引標籤和 [ [組建]](#build-tab) 索引標籤中變更 c # 專案 debug 設定。

若要開啟屬性頁，請在 **方案總管** 中選取專案，然後選取 [ **屬性** ] 圖示，或以滑鼠右鍵按一下專案，然後選取 [ **屬性**]。

如需詳細資訊，請參閱 [Debug 和 release](how-to-set-debug-and-release-configurations.md)設定。

>[!IMPORTANT]
>這些設定不適用於 .NET Core、ASP.NET 或 UWP 應用程式。 若要設定 UWP 應用程式的偵錯工具設定，請參閱 [啟動 uwp 應用程式的偵錯工具](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。

## <a name="debug-tab"></a>[偵錯] 索引標籤

|設定|Description|
|-------------------------------------| - |
| **Configuration** | 設定用來建立應用程式的模式。 從下拉式清單中選取 [ **Active (debug)**]、[ **debug**]、[ **Release**] 或 [ **所有** 設定]。 |
| **開始動作** | 指定當您在調試設定中選取 [ **啟動** ] 時的動作。<br />- [**啟動專案**] 是預設值，並且會啟動啟始專案以進行偵錯工具。 如需詳細資訊，請參閱 [選擇啟始專案](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))。<br />- **啟動外部程式** 啟動，並附加至不屬於專案的應用程式 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 如需詳細資訊，請參閱 [使用偵錯工具附加至執行中的進程](attach-to-running-processes-with-the-visual-studio-debugger.md)。<br />- **使用 URL 啟動瀏覽器** 可讓您對 web 應用程式進行偵錯工具。 |
| **開始選項**  > **命令列引數** | 指定要進行偵錯工具的命令列引數。 命令名稱是在 [ **啟動外部程式**] 中指定的應用程式名稱。 |
| **開始選項**  > **工作目錄** | 指定正在進行調試的應用程式的工作目錄。 在 c # 中，預設會 *\bin\debug* 工作目錄。
| **開始選項**  > **使用遠端電腦**|針對 [遠端偵錯程式]，選取此選項並輸入遠端偵錯程式目標的名稱，或輸入 [Msvsmon 伺服器名稱](../debugger/remote-debugging.md)。 <br />遠端電腦上應用程式的位置是由 [**組建**] 索引標籤上的 [**輸出路徑**] 屬性所指定。位置必須是遠端電腦上的可共用目錄。
| **偵錯工具引擎**  > **啟用非受控程式碼調試** 程式 | 從受管理的應用程式，對原生 (非受控) Win32 程式碼進行的呼叫。 |
| **偵錯工具引擎**  > **啟用 SQL Server 的調試** | SQL Server 資料庫物件進行調試。 |

## <a name="build-tab"></a>建置索引標籤

|設定|Description|
|-------------|-----------------|
|**一般**  > **條件式編譯符號**|如果已選取，請定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用 [Debug 類別](/dotnet/api/system.diagnostics.debug)和 [Trace 類別](/dotnet/api/system.diagnostics.trace)的條件式編譯。 完成這些常數定義之後，Debug 和 Trace 類別方法即會於[輸出視窗](../ide/reference/output-window.md)產生輸出。 如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br />通常，DEBUG 是在組建的 Debug 版本中定義，而且在發行版本中未定義。 追蹤是在 Debug 和 Release 版本中定義的。|
|**一般**  > **優化程式碼**|除非 bug 只出現在優化程式碼中，否則請將此設定保留為 [偵錯工具組建] 取消選取。 優化程式碼比較難進行偵錯工具，因為指令不會直接對應到原始程式碼中的語句。|
|**輸出**  > **輸出路徑**|通常會設定為 *bin\Debug* 進行偵錯工具。|
|**Advanced** 按鈕|如需 advanced 偵錯工具選項的詳細資訊，請參閱 [ (c # ) 的 [advanced build settings] 對話方塊 ](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。 符號 (*.pdb*) 檔案的可移植格式是適用于 .net Core 應用程式的最新跨平臺格式。

## <a name="see-also"></a>另請參閱
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)