---
title: Visual Studio 獨立模式 Shell |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 01917b9e78ee6129f09811ca2dc3e18c149c06f6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850381"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 獨立模式 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 獨立模式 Shell 可讓您建立能夠與其他 Visual Studio 版本並行執行的獨立應用程式。 它主要是用來裝載可使用 Visual Studio 服務，但也有自訂外觀和商標的特殊工具。 您可以輕鬆地開啟和關閉 Visual Studio 功能和功能表命令群組。 應用程式標題、應用程式圖示和啟動顯示畫面可以完全自訂。 如需可自訂功能的清單，請參閱[自訂獨立模式 Shell](../extensibility/customizing-the-isolated-shell.md)。  
  
 若要使用獨立的 shell 專案，您必須安裝 Visual Studio SDK。 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 若要建立獨立的 shell 應用程式，請從 Visual Studio Shell 隔離專案開始。 此專案包含開發和測試您自己的獨立 shell 應用程式所需的所有專案。 當您準備好要撰寫可部署應用程式的安裝程式時，您必須從[Microsoft Visual Studio shell （獨立模式）](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J)可轉散發套件取得獨立的 shell 可轉散發套件。  
  
> [!NOTE]
> 您必須先填寫簡短的客戶問卷，才可以存取獨立的 shell 可轉散發套件。  填完問卷後系統會將您導向至 Visual Studio Connect 頁面，內含可轉散發套件的下載連結。  您可以在後續造訪   **&#124; VISUAL Studio 2015 整合模式和獨立模式 SHELL**  索引標籤底下的 Visual Studio Connect 網站上找到下載連結。  
  
> [!NOTE]
> 如需如何部署獨立的 shell 型應用程式的詳細資訊，請參閱[逐步解說：建立基本的獨立模式 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="working-with-the-isolated-shell"></a>使用獨立模式 shell  
 Visual Studio 獨立模式的 shell 應用程式具有 Visual Studio 服務的完整存取權，並支援特殊的自訂和商標。 有數種方式可供您自訂獨立的 shell 應用程式：  
  
- 您可以使用 Vspackage 和 Managed Extensibility Framework （MEF）元件部分擴充獨立的 shell 應用程式，就像在任何其他 Visual Studio 延伸模組中使用它們一樣。 如需詳細資訊，請參閱[擴充獨立模式 Shell](../extensibility/extending-the-isolated-shell.md)。  
  
- 若要讓 Visual Studio 功能和功能表命令群組可用或無法使用，請更新應用程式的使用者介面（UI）專案中的 .vsct 檔案。  
  
- 若要從應用程式移除**選項**頁或其他 Visual Studio shell 元件，請更新應用程式的 .pkgundef 檔案。  
  
- 若要修改 shell 外觀或行為的其他層面，請更新應用程式的 .pkgdef 檔案。  
  
- 啟動應用程式時，也可以指定 shell 的某些層面。 若要這麼做，請將呼叫中的參數更新為 appenvstub 的開始進入點。  
  
  如需可自訂之不同元素的詳細資訊，請參閱[獨立模式 Shell 的元素](../extensibility/elements-of-the-isolated-shell.md)。  
  
## <a name="standard-features-of-the-isolated-shell"></a>獨立模式 Shell 的標準功能  
 以下是所有版本 Visual Studio 的標準功能。  
  
|功能分類|特殊功能|  
|----------------------|-------------|  
|IDE 功能|匯入/匯出設定<br /><br /> 工具箱控制項安裝程式<br /><br /> 工作清單 & 錯誤清單<br /><br /> 輸出視窗<br /><br /> 起始網頁<br /><br /> 屬性視窗<br /><br /> 工具箱<br /><br /> 底下提供說明，包括方案總管<br /><br /> 書籤視窗<br /><br /> 類別檢視<br /><br /> 物件瀏覽器<br /><br /> 命令視窗<br /><br /> 文件大綱<br /><br /> 資源檢視<br /><br /> 外部工具<br /><br /> Windows Communication Foundation （WCF）加入服務參考<br /><br /> 語言整合式查詢（LINQ）支援|  
|編輯器/設計工具|程式碼流覽工具（整合尋找、來源定義、繼承）<br /><br /> IntelliSense<br /><br /> 智慧標籤<br /><br /> 程式碼片段管理員<br /><br /> 程式碼片段<br /><br /> Refactoring<br /><br /> 整齊清單<br /><br /> IntelliSense 篩選<br /><br /> 程式碼定義視窗<br /><br /> 應用程式設計工具<br /><br /> Windows Form 設計工具<br /><br /> Windows Presentation Foundation （WPF）設計工具|  
|偵錯|C#運算式評估工具<br /><br /> 本機偵錯<br /><br /> Managed 調試<br /><br /> 編輯後繼續<br /><br /> 跨執行緒的調試<br /><br /> 視覺效果<br /><br /> 資料提示方塊<br /><br /> 原生調試<br /><br /> 指令碼偵錯<br /><br /> Interop 調試<br /><br /> 及時（JIT）調試<br /><br /> 多處理序偵錯<br /><br /> XSLT 偵錯<br /><br /> 附加至本機進程<br /><br /> 追蹤點<br /><br /> 中斷點條件約束|  
|Data|伺服器總管（僅限資料）<br /><br /> 資料系結至本機資料（。MDF 或.MDB<br /><br /> 資料系結至物件<br /><br /> 資料系結至 Web 服務<br /><br /> 一組完整的資料控制項<br /><br /> XML 編輯器<br /><br /> 資料系結至本機資料庫伺服器<br /><br /> 資料來源視窗|  
|Web|HTML 編輯器<br /><br /> Web 瀏覽器<br /><br /> Web Form 設計工具<br /><br /> 網站專案<br /><br /> Web 應用程式專案|  
|擴充性|使用 Vspackage 和 MEF 元件|  
  
## <a name="see-also"></a>請參閱  
 [Shell (獨立模式或整合模式)](../extensibility/shell-isolated-or-integrated.md)
