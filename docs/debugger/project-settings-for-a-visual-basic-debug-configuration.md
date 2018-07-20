---
title: Visual Basic 偵錯組態的專案設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7e2a1d49b2fc65afb5573b5d5ae36cc01f29e16
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155591"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Project Settings for a Visual Basic Debug Configuration
您可以變更的專案設定[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]中的偵錯組態**屬性頁**視窗中所述[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。 下表顯示與偵錯工具相關的設定中的位置**屬性頁**視窗。  
  
> [!WARNING]
>  本主題不適用於 UWP 應用程式。 請參閱[啟動偵錯工作階段 (VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>偵錯索引標籤  
  
|設定|描述|  
|-------------|-----------------|  
|**組態**|設定應用程式的編譯模式。 選擇**現用 （偵錯）**，**偵錯**，**版本**，**所有組態**。|  
|**啟動動作**|這個控制項群組會指定當您從 [偵錯] 功能表選擇 [啟動] 時會發生的動作。<br /><br /> -   **啟動專案**是預設值，並啟動偵錯的啟始專案。 <br />-   **啟動外部程式**可讓您可以啟動並附加至程式不屬於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案。 如需詳細資訊，請參閱 <<c0> [ 附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。<br />-   **以 URL 啟動瀏覽器**可讓您偵錯 Web 應用程式。|  
|**命令列引數**|指定要偵錯的程式之命令列引數。 命令名稱是在 [啟動外部程式] 指定的程式名稱。 如果將 [啟動動作] 設為 [起始 URL]，便會忽略命令列引數。|  
|**工作目錄**|指定為程式偵錯時的工作目錄。 在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，工作目錄為啟動應用程式的目錄。 預設工作目錄為 \bin\Debug 或 \bin\Release，視目前組態而定。|  
|**使用遠端電腦**|選取核取方塊時，即啟用遠端偵錯。 在文字方塊中，您可以輸入名稱以進行偵錯的遠端電腦將執行應用程式或[Msvsmon 伺服器名稱](../debugger/remote-debugging.md)。 遠端機器上的 EXE 位置可在 [建置] 索引標籤的 [輸出路徑] 屬性中指定。其位置必須是遠端電腦上的可共用目錄。|  
|**Unmanaged 程式碼偵錯**|讓您可以從 Managed 應用程式偵錯原生 (Unmanaged) Win32 程式碼的呼叫。 這個動作與在 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案中選取 [偵錯工具類型的混合模式] 具有相同效果。|  
|**SQL Server 偵錯**|允許 SQL Server 資料庫物件偵錯。|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>編譯索引標籤：按下進階編譯選項按鈕  
  
|設定|描述|  
|-------------|-----------------|  
|**啟用最佳化**|一定要取消勾選這個選項。 最佳化會讓實際執行的程式碼，與 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中所見的原始程式碼不同，導致偵錯更加困難。 如果對程式碼進行最佳化，則使用 Just My Code 進行偵錯時，預設為不載入符號。|  
|**產生偵錯資訊**|預設已定義在偵錯版本和發行版本中，此設定 (相當於 /debug 編譯器選項) 會在建置期間建立偵錯資訊。 偵錯工具會在偵錯時，使用這份資訊以有用的格式顯示變數名稱和其他資訊。 如果您沒有用這份資訊來編譯程式，偵錯工具的功能便會有所侷限。 如需詳細資訊，請參閱 < [/ 偵錯](/dotnet/visual-basic/reference/command-line-compiler/debug)。|  
|**定義 DEBUG 常數**|定義這個符號可以啟用條件式編譯的輸出函式，從[Debug 類別](/dotnet/api/system.diagnostics.debug)。 定義這個符號，Debug 類別方法會產生輸出[輸出視窗](../ide/reference/output-window.md)。 如果沒有這個符號，Debug 類別方法便不會編譯，也不會產生輸出。 這個符號應該會定義在偵錯版本，且不會定義在發行版本中。 在發行版本定義這個符號會建立減慢程式速度的無用程式碼。|  
|**定義 TRACE 常數**|定義這個符號可以啟用條件式編譯的輸出函式，從[Trace 類別](/dotnet/api/system.diagnostics.trace)。 定義這個符號，Trace 類別方法會產生輸出[輸出視窗](../ide/reference/output-window.md)。 如果沒有這個符號，Trace 類別方法便不會編譯，且不會產生輸出。 根據預設，這個符號已定義於偵錯版本和發行版本中。|  
  
## <a name="see-also"></a>另請參閱  
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)