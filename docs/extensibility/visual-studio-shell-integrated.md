---
redirect_url: shell/visual-studio-shell-integrated
title: "Visual Studio Shell （整合模式） |Microsoft 文件"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b43e4ac1c8e40a9f4f378be42cc642767bee0777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell （整合模式）
Visual Studio 整合式 shell 包括整合式的開發環境 (IDE)、 偵錯工具，以及原始檔控制整合。 不隨附的任何程式語言。 但是，整合式的 shell 並提供此架構可讓您將加入的程式語言。  
  
 Visual Studio 整合式 shell 是實際的 Visual Studio isolated shell 加上額外安裝包含整合式的 shell 特定元件的組合。  整合式的 shell 應用程式應該包含這兩個獨立的 shell 可轉散發套件的[Microsoft Visual Studio Shell （隔離式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616022)以及整合式的 shell 可轉散發套件從[Microsoft Visual Studio Shell （整合式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616021)。  
  
> [!NOTE]
>  您可以存取的隔離和整合式 shell 可轉散發套件之前，系統會要求您填寫客戶簡短問卷調查。  填寫問卷之後, 您將會導向至可轉散發套件下載連結的 Visual Studio 連接頁面。  您可以找到下載連結至 Visual Studio 連接的站台，在後續造訪**程式 &#124;VISUAL STUDIO 2015 整合式和 ISOLATED SHELL**  索引標籤。  
  
 如果您安裝完整版的 Visual Studio 的同一部電腦上的整合式的 shell 應用程式，將會直接在 Visual Studio 整合您的應用程式元件。  
  
## <a name="features-in-the-integrated-shell"></a>整合式 Shell 中的功能  
  
|||  
|-|-|  
|功能範圍|功能|  
|語言支援|-無|  
|IDE|<ul><li>設定<br /><br /> <ul><li>建立設定</li><li>匯入和匯出設定</li><li>重設設定</li></ul></li><li>**工具箱**整合</li><li>**工作清單**整合</li><li>說明整合</li><li>**選項**對話方塊</li><li>字型和色彩管理</li><li>**輸出**視窗</li><li>**命令**視窗</li><li>視窗管理</li><li>命令、 功能表和索引鍵繫結</li><li>特定領域語言 (DSL) 執行階段</li></ul>|  
|專案系統和專案類型|-解決方案和方案資料夾<br />方案組態管理員<br />項目管理<br />-單一專案和多專案方案<br />應用程式的設計工具 （簡化的專案屬性）<br />加入 Web 參考<br />加入服務參考<br />-單一專案<br />-網站專案類型<br />-Web 應用程式專案|  
|組建|的在 IDE 中自訂建置步驟<br />預先編譯的智慧財產權 (IP) 保護<br />程式碼簽署<br />     MSBuild|  
|編輯器|程式碼瀏覽工具統一的尋找、 來源定義 （繼承）<br />程式碼瀏覽<br />-IntelliSense<br />-智慧標籤<br />-重構<br />-美化<br />-IntelliSense 篩選<br />-   **程式碼定義**視窗|  
|Designer|Windows Presentation Foundation 設計工具<br />Windows Form 設計工具<br />-Web 設計工具] 和 [HTML 編輯器|  
|資料|-   **伺服器總管**(簡體： 僅限資料)。 請參閱「注意 1」。<br />-   **資料來源**視窗<br />-的整組資料控制項<br />XML 編輯器<br />資料繫結至本機資料來源 (。MDF 或。MDB)<br />資料繫結至物件<br />資料繫結至 Web 服務<br />資料繫結到本機資料庫伺服器<br />資料繫結到遠端資料庫伺服器<br />-DDL 工具的遠端資料<br />-   **伺服器總管**擴充性 ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]範例)|  
|偵錯工具|本機偵錯。 請參閱附註 2。<br />-Managed 偵錯<br />本機偵錯<br />附加至本機處理序<br />附加至遠端程序<br />匿名委派<br />-應用程式定義域<br />-ASPX 偵錯<br />-屬性<br />-中斷期間 eval 函式<br />-中斷點<br />中斷點條件約束<br />-呼叫堆疊<br />-   **命令**視窗<br />-跨執行緒偵錯<br />資料提示<br />資料視覺化檢視<br />Managed 偵錯助理 (Mda) 的偵錯支援<br />-類型轉送子偵錯工具支援<br />-DTEEvents OTB 支援<br />-JMC Stepper<br />偵錯 AppID 測試 (DBGCLR)<br />偵錯設定檔<br />-偵錯工具的工具和選項<br />-偵錯迭代器<br />為設計階段運算式評估<br />-C# 運算式評估工具<br />-反組譯碼<br />-編輯後繼續<br />運算式評估工具視窗 (監看式區域變數，[自動變數])<br />-例外狀況協助程式<br />例外狀況<br />-執行<br />-   泛型<br />-取得正確的來源<br />HPC/叢集偵錯<br />整合多語言偵錯<br />-InterOp 偵錯<br />-在 just-in-time 偵錯<br />本機偵錯<br />-Managed 偵錯<br />-手動控制 （處理序 視窗）<br />記憶體<br />-小型傾印支援<br />-模組<br />-多處理序偵錯<br />原生偵錯<br />-新的偵錯引擎支援<br />-最佳化程式碼偵錯<br />篩選輸出視窗<br />-處理裝載進行 managed 偵錯<br />-處理序<br />-快速監看式<br />-暫存器<br />堆疊中註冊<br />-遠端偵錯<br />傳回值<br />指令碼偵錯<br />原始碼服務支援<br />安全性<br />---並存<br />SQL<br />符號伺服器<br />追蹤點<br />執行緒<br />-視覺效果<br />-可延伸樣式表語言轉換 (XSLT) 偵錯工具|  
|64 位元支援|-64 位元偵錯 managed 和原生程式碼中，所有語言<br />-x64 原生支援|  
|原始程式碼控制 (SCC)|-基本 SCC 整合。 請參閱「注意 3」。<br />-工具和選項，驗證|  
|擴充性|-使用 Vspackage 和 MEF 元件|  
  
## <a name="notes"></a>注意  
  
#### <a name="1-data-tools"></a>1.資料工具  
 整合式的 shell 包含資料庫開發工具，例如資料擴充性支援並簡化**方案總管 中**。 不過，不會包含 SQL Server Express 和 SQL 報表，並採用的 Crystal Reports 整合式 shell 中。  
  
#### <a name="2-debugging-support"></a>2.偵錯支援  
 整合式的 shell 包括隨附於 Visual Studio Community 版是相同的偵錯引擎。 偵錯引擎包含常見的偵錯工具 managed 程式碼，以及相關的功能，例如附加、 設定中斷點、 編輯後繼續 」，以及其他人執行。 不過，偵錯引擎不支援 SQL Server 資料庫偵錯。  
  
 雖然支援原生偵錯，就會包括基本的偵錯工具封裝，您無法擴充，以支援其他語言。  
  
#### <a name="3-source-code-control-integration"></a>3.原始程式碼控制整合  
 整合式的 shell 提供應用程式開發介面，以實作原始程式碼控制 (SCC) 並提供 MSSCCI 基礎通用的原始檔控制整合元件。  
  
 雖然 SCC 整合不是一般的 Visual Studio 的 Pro 版本的功能，會提供整合式 shell SCC 整合。  
  
#### <a name="4-build-support"></a>4.建置支援  
 整合式的 shell 提供建置支援。 您可以找到資訊中的組建[MSBuild 參考](../msbuild/msbuild-reference.md)。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>並未包含在整合式 Shell 中的功能  
 以下是不包含在整合式 shell 的功能清單：  
  
-   類別設計工具  
  
-   [先佔式保護-Dotfuscator](../ide/dotfuscator/index.md)  
  
-   語言功能  
  
-   VSHost  
  
-   沒有 Visual Studio 語言，或其相關聯的專案範本或專案項目範本，會包含在整合式 shell。 語言特有的任何實作其他功能不是，針對 Visual Basic 程式碼片段的範例。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)