---
title: 專案設定為C#偵錯組態 |Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
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
ms.openlocfilehash: 7152e6ac16c8a15ba6973eb3ac33c373560a0d76
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388961"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# 偵錯組態的專案設定

您可以變更C#專案中的偵錯設定[偵錯 索引標籤](#debug-tab)並[建置 索引標籤](#build-tab)專案屬性頁。 

若要開啟屬性頁面，選取 在專案**方案總管**，然後選取**屬性**圖示，或以滑鼠右鍵按一下專案，然後選取**屬性**。

如需詳細資訊，請參閱[偵錯和發行組態](how-to-set-debug-and-release-configurations.md)。 

>[!IMPORTANT]
>這些設定不適用於.NET Core、 ASP.NET 或 UWP 應用程式。 若要設定之 UWP 應用程式的偵錯設定，請參閱[啟動的 UWP 應用程式的偵錯工作階段](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。  
  
## <a name="debug-tab"></a>偵錯索引標籤  
  
|設定|描述|
|-------------------------------------| - |
| **組態** | 建置應用程式的設定模式。 選取 **現用 （偵錯）**，**偵錯**，**版本**，或**所有組態**從下拉式清單。 |
| **起始動作** | 指定的動作，當您選取**啟動**偵錯組態。<br />- [起始專案] 是預設動作，並且會啟動用於偵錯的啟始專案。 如需詳細資訊，請參閱 <<c0> [ 選擇啟始專案](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))。<br />- **啟動外部程式**開始，並將附加至應用程式不屬於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 如需詳細資訊，請參閱 <<c0> [ 附加至執行中處理序偵錯工具](attach-to-running-processes-with-the-visual-studio-debugger.md)。<br />- **以 URL 啟動瀏覽器**可讓您偵錯 web 應用程式。 |
| **起始選項** > **命令列引數** | 指定正在進行偵錯的應用程式的命令列引數。 命令名稱是在指定的應用程式名稱**啟動外部程式**。 |
| **起始選項** > **工作目錄** | 指定應用程式進行偵錯的工作目錄。 在C#，工作目錄*\bin\debug*預設。
| **起始選項** > **使用遠端電腦**|遠端偵錯，請選取此選項，然後輸入名稱的遠端偵錯目標，或[Msvsmon 伺服器名稱](../debugger/remote-debugging.md)。 <br />在遠端電腦上的應用程式的位置由**輸出路徑**屬性上的**建置** 索引標籤。其位置必須是遠端電腦上的可共用目錄。 
| **偵錯工具引擎** > **啟用 unmanaged 程式碼偵錯** | 從受管理的應用程式呼叫原生 (unmanaged) Win32 程式碼進行偵錯。 |
| **偵錯工具引擎** > **啟用 SQL Server 偵錯** | 偵錯 SQL Server 資料庫物件。 |
  
## <a name="build-tab"></a>建置索引標籤  
  
|設定|描述|  
|-------------|-----------------|  
|**一般** > **條件式編譯符號**|如果選取，請定義 DEBUG 和 TRACE 常數。<br /><br /> 這些常數可啟用 [Debug 類別](/dotnet/api/system.diagnostics.debug)和 [Trace 類別](/dotnet/api/system.diagnostics.trace)的條件式編譯。 完成這些常數定義之後，Debug 和 Trace 類別方法即會於[輸出視窗](../ide/reference/output-window.md)產生輸出。 如果沒有這些常數，Debug 和 Trace 類別方法便不會編譯，且不會產生輸出。<br /><br />通常，偵錯是定義在偵錯版本的組建和發行版本中未定義。 追蹤已定義在偵錯和發行版本。|  
|**一般** > **最佳化程式碼**|除非錯誤只會出現在最佳化程式碼，否則請保留 偵錯組建的 已取消選取此設定。 最佳化程式碼較難偵錯，因為直接至在原始程式碼中的陳述式沒有對應的指示。|  
|**輸出** > **輸出路徑**|偵錯通常會設為 *bin\Debug*。|
|**進階**按鈕|如需進階偵錯選項的資訊，請參閱[進階的建置設定對話方塊 (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)。 符號的可攜式格式 (*.pdb*) 檔案是最新的跨平台格式，.NET Core 應用程式。 
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)