---
title: "C# 偵錯組態的專案設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
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
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d588f43271b127c675a6ec2fdf9e55ef388eadf2
ms.sourcegitcommit: 1e08318a8a684b21609af7a5e48b56abcc3239e6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 偵錯組態的專案設定
您可以變更 C# 偵錯組態中的專案設定**屬性頁**視窗中所述[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。 下表顯示如何尋找中的偵錯工具相關設定**屬性頁**視窗。  
  
> [!WARNING]
>  本主題不適用於 UWP 和 Windows 8.1 應用程式。 請參閱[開始偵錯工作階段 （VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a>偵錯索引標籤  
  
|**設定**|**說明**|  
|-----------------|---------------------|  
|**組態**|設定應用程式的編譯模式。 選擇**現用 （偵錯）**，**偵錯**，**發行**，**所有組態**。|  
|**起始動作**|這個控制項群組會指定當您從 [偵錯] 功能表選擇 [啟動] 時會發生的動作。<br /><br /> -   **啟動專案**是預設值，並啟動偵錯的啟始專案。 如需詳細資訊，請參閱[選擇啟始專案](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd)。<br />-   **啟動外部程式**可讓您啟動並附加至不是程式的一部分[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 如需詳細資訊，請參閱[附加到執行程式](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)。<br />-   **以 URL 啟動瀏覽器**可讓您偵錯 Web 應用程式。|  
|**命令列引數**|指定要偵錯的程式之命令列引數。 命令名稱是在 [啟動外部程式] 指定的程式名稱。 如果 [啟動動作] 設為 [起始 URL]，便不能指定命令列引數。|  
|**工作目錄**|指定為程式偵錯時的工作目錄。 在 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\bin\debug。|  
|**使用遠端電腦**|以進行偵錯的遠端電腦執行應用程式所在的名稱或[Msvsmon 伺服器名稱](../debugger/remote-debugging.md)。 遠端機器上 EXE 的位置是從 [建置] 分類、[組態屬性] 資料夾中的 [輸出路徑] 屬性中所指定。 其位置必須是遠端電腦上的可共用目錄。|
|**啟用 Unmanaged 程式碼偵錯**|讓您可以從 Managed 應用程式偵錯原生 (Unmanaged) Win32 程式碼的呼叫。|  
|**啟用 SQL Server 偵錯**|允許 SQL Server 資料庫物件偵錯。|  
  
##  <a name="BKMK_Build_tab"></a>建置索引標籤  
  
|設定|說明|  
|-------------|-----------------|  
|**條件式編譯符號：**|此處會定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用的條件式編譯[Debug 類別](/dotnet/api/system.diagnostics.debug)和[Trace 類別](/dotnet/api/system.diagnostics.trace)。 使用這些常數定義之後，偵錯和 Trace 類別方法會產生輸出[輸出 視窗](../ide/reference/output-window.md)。 如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br /> 偵錯通常是定義在程式的偵錯版本，而且未在發行版本中定義。<br />追蹤通常會定義在偵錯和發行版本。|  
|**最佳化程式碼**|除非您發現一個僅出現在最佳化程式碼裡的錯誤，否則您應該在偵錯版本裡關閉這個設定。 因為指令無法直接對應到來源視窗的陳述式，所以較難偵錯最佳化程式碼。|  
|**輸出路徑：**|偵錯通常會設為 bin\Debug。|

> [!NOTE]
> 如需有關您在中找到的偵錯選項**進階**按鈕，請參閱[進階建置設定對話方塊 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。 符號 (.pdb) 檔案的可攜式格式是.NET Core 的最新的跨平台格式。 
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)