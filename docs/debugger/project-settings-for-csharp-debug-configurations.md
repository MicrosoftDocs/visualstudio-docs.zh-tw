---
title: C# 偵錯組態的專案設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a65928e8a5a734e84d51cbb4368c7346ba8c2edb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896337"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 偵錯組態的專案設定
您可以變更專案設定中的 C# 偵錯組態**屬性頁**視窗中所述[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。 下表顯示與偵錯工具相關的設定中的位置**屬性頁**視窗。  
  
> [!WARNING]
>  本主題不適用於 UWP 應用程式。 請參閱[啟動偵錯工作階段 (VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> 偵錯 索引標籤  
  
| **設定** | **描述** |
|-------------------------------------| - |
| **組態** | 設定應用程式的編譯模式。 選擇**現用 （偵錯）**，**偵錯**，**版本**，**所有組態**。 |
| **啟動動作** | 這個控制項群組會指定當您從 [偵錯] 功能表選擇 [啟動] 時會發生的動作。<br /><br /> -   **啟動專案**是預設值，並啟動偵錯的啟始專案。 如需詳細資訊，請參閱 <<c0> [ 選擇啟始專案](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))。<br />-   **啟動外部程式**可讓您可以啟動並附加至程式不屬於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 如需詳細資訊，請參閱 <<c0> [ 附加至正在執行的程式](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z(v=vs.100))。<br />-   **以 URL 啟動瀏覽器**可讓您偵錯 Web 應用程式。 |
| **命令列引數** | 指定要偵錯的程式之命令列引數。 命令名稱是在 [啟動外部程式] 指定的程式名稱。 如果 [啟動動作] 設為 [起始 URL]，便不能指定命令列引數。 |
| **工作目錄** | 指定為程式偵錯時的工作目錄。 在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\bin\debug。 |
| **使用遠端電腦** | 遠端應用程式將執行的電腦以進行偵錯的名稱或[Msvsmon 伺服器名稱](../debugger/remote-debugging.md)。 遠端機器上 EXE 的位置是從 [建置] 分類、[組態屬性] 資料夾中的 [輸出路徑] 屬性中所指定。 其位置必須是遠端電腦上的可共用目錄。 |
| **啟用 Unmanaged 程式碼偵錯** | 讓您可以從 Managed 應用程式偵錯原生 (Unmanaged) Win32 程式碼的呼叫。 |
| **啟用 SQL Server 偵錯** | 允許 SQL Server 資料庫物件偵錯。 |
  
##  <a name="BKMK_Build_tab"></a> 建置索引標籤  
  
|設定|描述|  
|-------------|-----------------|  
|**條件式編譯符號：**|此處會定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用的條件式編譯[Debug 類別](/dotnet/api/system.diagnostics.debug)並[Trace 類別](/dotnet/api/system.diagnostics.trace)。 使用這些常數定義之後，偵錯和 Trace 類別方法產生的輸出[輸出視窗](../ide/reference/output-window.md)。 如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br /> 偵錯通常定義於程式的偵錯版本，且未定義的發行版本中。<br />-追蹤通常會定義在偵錯和發行版本。|  
|**最佳化程式碼**|除非您發現一個僅出現在最佳化程式碼裡的錯誤，否則您應該在偵錯版本裡關閉這個設定。 因為指令無法直接對應到來源視窗的陳述式，所以較難偵錯最佳化程式碼。|  
|**輸出路徑：**|偵錯通常會設為 bin\Debug。|

> [!NOTE]
> 如需有關您在中找到的偵錯選項**進階**按鈕，請參閱[進階建置設定對話方塊 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。 可攜式符號 (.pdb) 檔案格式是最新的跨平台格式，適用於.NET Core。 
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)