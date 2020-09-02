---
title: 'C # Debug 設定的專案設定 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687523"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 偵錯組態的專案設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 [ **屬性頁** ] 視窗中變更 c # debug 設定的專案設定，如 [debug 和 Release](../debugger/how-to-set-debug-and-release-configurations.md)設定中所述。 下表顯示 [屬性頁]**** 視窗中，偵錯工具相關設定的位置。  
  
> [!WARNING]
> 本主題不適用於 Windows 市集應用程式。 請參閱 [開始 (VB、c #、c + + 和 XAML 的 debug 會話) ](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> [調試] 索引標籤  
  
|**設定**|**說明**|  
|-----------------|---------------------|  
|**設定**|設定應用程式的編譯模式。 請選擇 [現用 (偵錯)]****、[偵錯]****、[發行]**** 或 [所有組態]**** 其中之一。|  
|**啟動執行**|這個控制項群組會指定當您從 [偵錯] 功能表選擇 [啟動] 時會發生的動作。<br /><br /> -   [起始專案]**** 是預設動作，並且會啟動用於偵錯的啟始專案。 如需詳細資訊，請參閱 [選擇啟始專案](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd)。<br />-   [啟動外部程式]**** 讓您可以啟動並附加至不屬於 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案一部分的程式。 如需詳細資訊，請參閱 [附加至正在執行的程式](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)。<br />-   [以 URL 啟動瀏覽器]**** 可讓您偵錯 Web 應用程式。|  
|**命令列引數**|指定要偵錯的程式之命令列引數。 命令名稱是在 [啟動外部程式] 指定的程式名稱。 如果 [啟動動作] 設為 [起始 URL]，便不能指定命令列引數。|  
|**工作目錄**|指定為程式偵錯時的工作目錄。 在 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 中，工作目錄預設為啟動應用程式的來源目錄：\bin\debug。|  
|**使用遠端電腦**|將執行應用程式以進行偵測的遠端電腦名稱稱，或為 [Msvsmon 伺服器名稱](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c)。 遠端機器上 EXE 的位置是從 [建置] 分類、[組態屬性] 資料夾中的 [輸出路徑] 屬性中所指定。 其位置必須是遠端電腦上的可共用目錄。|  
|**啟用 Unmanaged 程式碼偵錯**|讓您可以從 Managed 應用程式偵錯原生 (Unmanaged) Win32 程式碼的呼叫。|  
|**啟用 SQL Server 偵錯**|允許 SQL Server 資料庫物件偵錯。|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> [組建] 索引標籤  
  
|設定|描述|  
|-------------|-----------------|  
|**條件式編譯符號：**|此處會定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用 [Debug 類別](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx)和 [Trace 類別](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx)的條件式編譯。 完成這些常數定義之後，Debug 和 Trace 類別方法即會於[輸出視窗](../ide/reference/output-window.md)產生輸出。 如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br /> -Debug 通常是在程式的 Debug 版本中定義，而且在發行版本中未定義。<br />-追蹤通常定義于 Debug 和發行版本中。|  
|**最佳化程式碼**|除非您發現一個僅出現在最佳化程式碼裡的錯誤，否則您應該在偵錯版本裡關閉這個設定。 因為指令無法直接對應到來源視窗的陳述式，所以較難偵錯最佳化程式碼。|  
|**輸出路徑：**|偵錯通常會設為 bin\Debug。|  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定及準備](../debugger/debugger-settings-and-preparation.md)
