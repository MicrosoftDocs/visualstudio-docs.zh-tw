---
title: Visual Studio 獨立模式 Shell |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed81e88b12e371f74adb9d3911719112bca8b139
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499076"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 獨立模式 Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[Visual Studio Isolated Shell](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-isolated-shell)。  
  
Visual Studio 獨立模式 shell 可讓您建立獨立的應用程式可執行並排顯示與其他版本的 Visual Studio。 就用主要是用來裝載專門的工具，可以使用 Visual Studio 服務，但也有自訂的外觀及商標。 Visual Studio 功能和功能表命令群組可以輕鬆地開啟和關閉。 應用程式標題、 應用程式圖示和啟動顯示畫面都開放完全自訂。 如需可自訂的功能，請參閱[自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)。  
  
 若要使用的獨立的 shell 專案，您必須安裝 Visual Studio SDK。 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
 若要建立 isolated 的 shell 應用程式，開始使用 Visual Studio Shell 獨立模式的專案。 此專案包含您要開發和測試您自己的 isolated 的 shell 應用程式的所有項目。 當您準備好開始撰寫安裝程式，以部署您的應用程式時，您必須取得獨立模式的 shell 可轉散發套件，從[Microsoft Visual Studio Shell （獨立模式） 可轉散發套件](http://go.microsoft.com/fwlink/?LinkId=616022)。  
  
> [!NOTE]
>  您可以存取獨立模式的 shell 可轉散發套件之前，系統會要求您填寫簡短的客戶問卷調查。  在填寫問卷之後, 您會導向至 Visual Studio Connect 頁面可轉散發套件下載連結。  您可以在後續造訪 Visual Studio Connect 網站的 [下找到的下載連結**程式&#124;VISUAL STUDIO 2015 整合和 ISOLATED SHELL** ] 索引標籤。  
  
> [!NOTE]
>  如需如何部署獨立 shell 應用程式的詳細資訊，請參閱[逐步解說： 建立基本獨立 Shell 應用程式](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)。  
  
## <a name="working-with-the-isolated-shell"></a>使用 獨立模式 shell  
 Visual Studio isolated shell 應用程式具有完整存取權 Visual Studio 服務，並支援特殊的自訂和商標。 有數種方式，您可以自訂 isolated 的 shell 應用程式：  
  
-   您可以使用 Vspackage 和 Managed Extensibility Framework (MEF) 元件組件來擴充 isolated 的 shell 應用程式，就像您其他 Visual Studio 延伸模組中使用它們。 如需詳細資訊，請參閱 <<c0> [ 擴充 Isolated Shell](../extensibility/extending-the-isolated-shell.md)。  
  
-   若要讓 Visual Studio 功能和功能表命令群組，可以或無法使用，更新.vsct 檔案中的應用程式的使用者介面 (UI) 專案。  
  
-   若要移除**選項**頁面或應用程式，從其他 Visual Studio shell 元件更新.pkgundef 檔案的應用程式。  
  
-   若要修改其他方面的外觀或行為的殼層，更新應用程式的.pkgdef 檔。  
  
-   只有當應用程式啟動時，也可以指定殼層的某些層面。 若要這樣做，請更新 appenvstub.dll 開始進入點的呼叫中的參數。  
  
 如需您可以自訂的不同元素的詳細資訊，請參閱[Isolated Shell 的項目](../extensibility/elements-of-the-isolated-shell.md)。  
  
## <a name="standard-features-of-the-isolated-shell"></a>Isolated Shell 的標準功能  
 下列功能是標準的 Visual Studio 所有版本。  
  
|功能分類|功能|  
|----------------------|-------------|  
|IDE 功能|匯入/匯出設定<br /><br /> 工具箱控制項安裝程式<br /><br /> 工作清單] & [錯誤清單<br /><br /> 輸出視窗<br /><br /> 起始頁<br /><br /> 屬性視窗<br /><br /> 工具箱<br /><br /> 底下提供說明，包括方案總管<br /><br /> 書籤視窗<br /><br /> 類別檢視<br /><br /> 物件瀏覽器<br /><br /> 命令視窗<br /><br /> 文件大綱<br /><br /> 資源檢視<br /><br /> 外部工具<br /><br /> Windows Communication Foundation (WCF) 加入服務參考<br /><br /> Language-integrated Query (LINQ) 支援|  
|編輯器/設計工具|程式碼瀏覽工具合併的尋找、 來源定義 （繼承）<br /><br /> IntelliSense<br /><br /> 智慧標籤<br /><br /> 程式碼片段管理員<br /><br /> 程式碼片段<br /><br /> 重構<br /><br /> 美化排列<br /><br /> IntelliSense 篩選<br /><br /> 程式碼定義視窗<br /><br /> 應用程式設計工具<br /><br /> Windows Form 設計工具<br /><br /> Windows Presentation Foundation (WPF) 設計工具|  
|偵錯|C# 運算式評估工具<br /><br /> 本機偵錯<br /><br /> Managed 偵錯<br /><br /> 編輯後繼續<br /><br /> 跨執行緒偵錯<br /><br /> 視覺效果<br /><br /> 資料提示方塊<br /><br /> 原生偵錯<br /><br /> 指令碼偵錯<br /><br /> Interop 偵錯<br /><br /> 在 just-in-time (JIT) 偵錯<br /><br /> 多處理序偵錯<br /><br /> XSLT 偵錯<br /><br /> 附加至本機處理序<br /><br /> 追蹤點<br /><br /> 中斷點條件約束|  
|資料|伺服器總管 （簡體-僅限資料）<br /><br /> 資料繫結至本機資料 (。MDF 或。MDB)<br /><br /> 資料繫結至物件<br /><br /> 資料繫結至 Web 服務<br /><br /> 完整的資料控制項<br /><br /> XML 編輯器<br /><br /> 資料繫結至本機資料庫伺服器<br /><br /> 資料來源視窗|  
|Web|HTML 編輯器<br /><br /> 網頁瀏覽器<br /><br /> Web Form 設計工具<br /><br /> 網站專案<br /><br /> Web 應用程式專案|  
|擴充性|使用 Vspackage 和 MEF 元件|  
  
## <a name="see-also"></a>另請參閱  
 [Shell (獨立模式或整合模式)](../extensibility/shell-isolated-or-integrated.md)

