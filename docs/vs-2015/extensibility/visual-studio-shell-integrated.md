---
title: Visual Studio Shell （整合模式） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f6e88e5c430129faa80f34a45f9b6620d5b0d13
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850365"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (整合模式)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 整合模式 Shell 包含整合式開發環境 (IDE)、偵錯工具及原始檔控制整合。 未包含任何程式設計語言。 不過，整合式 shell 提供的架構可讓您新增程式設計語言。  
  
 Visual Studio 整合式 shell 實際上是 Visual Studio 獨立模式的組合，加上額外的安裝，其中包含整合式 shell 特定元件。  您的整合式 shell 應用程式應該包含來自[Microsoft Visual Studio shell （獨立模式）](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J)可轉散發套件的獨立 shell 可轉散發套件，以及來自[Microsoft Visual Studio shell （整合式）](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J)可轉散發套件的整合式 shell 可轉散發套件。  
  
> [!NOTE]
> 系統會先要求您填寫簡短的客戶問卷，之後您便可以存取獨立模式和整合模式 Shell 可轉散發套件。  填完問卷後系統會將您導向至 Visual Studio Connect 頁面，內含可轉散發套件的下載連結。  您可以在後續造訪   **&#124; VISUAL Studio 2015 整合模式和獨立模式 SHELL**  索引標籤底下的 Visual Studio Connect 網站上找到下載連結。  
  
 如果您將整合式 shell 應用程式安裝在與完整版 Visual Studio 相同的電腦上，您的應用程式元件將會直接整合到 Visual Studio。  
  
## <a name="features-in-the-integrated-shell"></a>整合式 Shell 中的功能  
  
|||  
|-|-|  
|功能區|特殊功能|  
|語言支援|-無|  
|IDE|<ul><li>設定<br /><br /> <ul><li>建立設定</li><li>匯入和匯出設定</li><li>重設設定</li></ul></li><li>**工具箱**整合</li><li>**工作清單**整合</li><li>協助整合</li><li>**選項**對話方塊</li><li>字型和色彩管理</li><li>**輸出**視窗</li><li>**命令**視窗</li><li>視窗管理</li><li>命令、功能表和按鍵系結</li><li>網域指定的語言（DSL）執行時間</li></ul>|  
|專案系統和專案類型|-解決方案和方案資料夾<br />-解決方案 configuration manager<br />-專案管理<br />-單一專案和多專案方案<br />-應用程式設計工具（簡化的專案屬性）<br />-加入 Web 參考<br />-加入服務參考<br />-單一專案<br />-網站專案類型<br />-Web 應用程式專案|  
|組建|-IDE 中的自訂群組建步驟<br />-適用于智慧財產（IP）保護的預先編譯<br />-程式碼簽署<br />     MSBuild|  
|編輯器|-程式碼流覽工具（整合尋找、來源定義、繼承）<br />-程式碼導覽<br />-IntelliSense<br />-智慧標籤<br />-重整<br />-整齊清單<br />-IntelliSense 篩選<br />-   程式**代碼定義**視窗|  
|Designer|-Windows Presentation Foundation 設計工具<br />-Windows Form 設計工具<br />-Web 設計工具和 HTML 編輯器|  
|Data|-   **伺服器總管**（簡化：僅限資料）。 請參閱「注意 1」。<br />-   **資料來源**視窗<br />-完整的資料控制項集<br />-XML 編輯器<br />-資料系結至本機資料來源（。MDF 或.MDB<br />-資料系結至物件<br />-資料系結至 Web 服務<br />-資料系結至本機資料庫伺服器<br />-資料系結至遠端資料庫伺服器<br />-遠端資料的 DDL 工具<br />-   **伺服器總管**擴充性（[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 範例）|  
|偵錯工具|-本機調試。 請參閱附注2。<br />-Managed 調試<br />-本機調試<br />-附加至本機進程<br />-附加至遠端進程<br />-匿名委派<br />-應用程式域<br />-ASPX 調試<br />-屬性<br />-Func 期間中斷-eval<br />-中斷點<br />-中斷點條件約束<br />-呼叫堆疊<br />-   **命令**視窗<br />-跨執行緒的調試<br />-資料提示<br />-資料視覺化檢視<br />-偵錯工具支援受管理的調試助理（Mda）<br />-類型轉寄站的偵錯工具支援<br />-OTB 的 DTEEvents 支援<br />-JMC 分檔器<br />-偵錯工具 AppID 測試（DBGCLR）<br />-偵錯工具設定檔<br />-偵錯工具工具和選項<br />-調試反覆運算器<br />-設計時程表達式評估<br />- C#運算式評估工具<br />-反組解碼<br />-編輯後繼續<br />-運算式評估工具視窗（監看式、區域變數、自動變數）<br />-例外狀況協助程式<br />-例外狀況<br />-執行<br />-   泛型<br />-取得正確的來源<br />-HPC/叢集調試<br />-整合式多語言調試<br />-InterOp 調試<br />-即時調試<br />-本機調試<br />-Managed 調試<br />-手動控制（進程視窗）<br />-   記憶體<br />-小型傾印支援<br />-模組<br />-多進程的偵錯工具<br />-原生調試<br />-新的 debug engine 支援<br />-優化程式碼調試<br />-輸出 windows 篩選<br />-進程裝載以進行 managed 偵錯工具<br />-進程<br />-快速監看式<br />-暫存器<br />-在堆疊中註冊<br />-遠端偵錯<br />-傳回值<br />-腳本調試<br />-來源服務支援<br />-安全性<br />-並存<br />-SQL<br />-符號伺服器<br />-追蹤點<br />-Thread<br />-視覺效果<br />-可擴充樣式單語言轉換（XSLT）偵錯工具|  
|64位支援|-64-適用于 managed 和機器碼（所有語言）的位偵錯工具<br />-x64 原生支援|  
|原始程式碼控制（SCC）|-基本 SCC 整合。 請參閱「注意 3」。<br />-工具和選項驗證|  
|擴充性|-使用 Vspackage 和 MEF 元件|  
  
## <a name="notes"></a>注意事項  
  
#### <a name="1-data-tools"></a>1. 資料工具  
 整合式 shell 包含資料庫開發工具，例如資料擴充性支援和簡化的**方案總管**。 不過，SQL Server Express、SQL Reporting 和 Crystal 報表不會包含在整合式 shell 中。  
  
#### <a name="2-debugging-support"></a>2. 調試支援  
 整合式 shell 包含 Visual Studio 的社區版本中所包含的相同偵錯工具引擎。 「偵錯工具引擎」包括適用于受控碼的一般偵錯工具，以及相關的功能，例如「執行」、「附加」、「設定中斷點」、「編輯後繼續」等等。 不過，調試引擎不支援 SQL Server 資料庫的調試。  
  
 雖然基本的偵錯工具封裝中包含原生偵測的支援，但您無法將它擴充以支援其他語言。  
  
#### <a name="3-source-code-control-integration"></a>3. 原始程式碼控制整合  
 整合式 shell 提供了用來執行原始程式碼控制（SCC）的 Api，以及提供以 MSSCCI 為基礎的通用原始檔控制整合元件。  
  
 雖然 SCC 整合不是 Pro 版 Visual Studio 的一般功能，但是整合式 shell 中提供了 SCC 整合。  
  
#### <a name="4-build-support"></a>4. 組建支援  
 整合式 shell 會提供組建支援。 您可以在[MSBuild 參考](../msbuild/msbuild-reference.md)中找到組建的相關資訊。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>未包含在整合式 Shell 中的功能  
 以下是未包含在整合式 shell 中的功能清單：  
  
- 類別設計工具  
  
- PreEmptive Protection - Dotfuscator  
  
- 語言功能  
  
- .Vshost.exe  
  
- 整合式 shell 中不會包含任何 Visual Studio 語言或其相關聯的專案範本或專案專案範本。 不包含其他功能的特定語言執行，例如 Visual Basic 程式碼片段。  
  
## <a name="see-also"></a>請參閱  
 [擴充 Visual Studio 總覽](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
