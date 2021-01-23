---
title: 效能工作階段概觀 | Microsoft Docs
description: 瞭解如何使用效能工具快速提升生產力，並提升您程式碼的效能。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1fcccf6a68afa26d8fe9ab5e5a4f40466822c689
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723266"
---
# <a name="performance-session-overview"></a>效能工作階段概觀
這個概觀說明程式碼剖析的基本概念。 接觸效能工作不久的開發人員將可見識 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 如何加速提升他們的生產力，並增進其程式碼的效能。 擁有豐富的程式碼剖析經驗的開發人員，則可獲得具體的程式碼剖析工具功能和處理程序的概觀。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具可協助您識別原始程式碼中的效能問題，並比較可行解決方法的效能。 程式碼剖析工具精靈和預設值可讓您立即洞悉許多效能問題。 程式碼剖析工具的功能和選項使您能夠精準控制程式碼剖析的處理程序。 這項控制包括精確指出程式碼區段、收集區塊層級的執行時間資訊，以及在您的資料中加入其他的處理器和系統效能資料。

 使用程式碼剖析工具的基本處理程序包含下列步驟：

1. 指定收集方法和要收集的資料，以設定效能工作階段。

2. 在效能工作階段中執行應用程式，以收集程式碼剖析資料。

3. 分析資料以識別效能問題。

4. 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境 (IDE) 中修改程式碼，以增加程式碼的應用程式效能。

5. 對變更過的程式碼收集程式碼剖析資料，並比較原始和變更資料的程式碼剖析資料。

6. 產生記錄效能提升的報告。

   若要使用程式碼剖析所提供的資訊，您必須有要剖析的二進位檔以及 Windows 作業系統的二進位檔之符號資訊。

## <a name="configure-the-performance-session"></a>設定效能工作階段
 若要設定程式碼剖析工作階段，請選取要使用的程式碼剖析方法以及要收集的資料。 程式碼剖析工具的 [效能精靈] 可以引導您完成基本的組態，您也可以使用 [效能工作階段] 屬性頁來加入其他選項：

- 程式碼剖析方法包括取樣、追蹤和記憶體配置。

- 資料值包含時間、處理器和作業系統效能計數器，以及應用程式事件，例如分頁錯誤和核心轉換。

  您可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案中將效能工作階段設定為專案方案的一部分，或透過 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 剖析任意二進位檔。 您可以在 [效能工作階段] 屬性頁中指定工作階段屬性，或使用程式碼剖析精靈。

## <a name="collect-profiling-data"></a>收集分析資料
 您可以從 [效能總管] 開始收集程式碼剖析資料。 您可以暫停和繼續分析，以限制資料收集量。 您也可以附加至已在執行中的處理序。

 只要一啟動應用程式，[資料收集控制] 視窗即會出現在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中。 從 [資料收集控制] 視窗中，藉由暫停和繼續收集處理序，即可對應用程式的特定部分進行程式碼剖析。 您也可以使用 [資料收集控制] 視窗，將標記插入收集到的資料中。 標記是使用者定義的資料點，這些資料點會顯示在程式碼剖析檢視中，而且可以用來篩選程式碼剖析資料。

 當目標應用程式關閉時，程式碼剖析工具會產生程式碼剖析資料檔 (*.vsp)，並在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 中顯示 [摘要報告] 檢視。

## <a name="analyze-the-data-and-identify-performance-issues"></a>分析資料和識別效能問題
 結束一個程式碼剖析執行後，會進行資料分析，並在程式碼剖析工具的 [效能報告] 檢視視窗中顯示摘要。 程式碼剖析資料的收集，是針對目標應用程式的呼叫堆疊和個別函式。 報告檢視所顯示的效能分析的資料範圍，包括應用程式的處理序、執行緒、模組、函式和原始程式碼行。 函式的程式碼剖析資料值包括下列項目：

- 函式和函式呼叫之子函式所花費的整體時間 (內含值)。

- 僅執行函式中之程式碼所花費的時間 (專有值)。

  有超過 12 種不同的檢視，可以讓您以最有效的方式分析程式碼剖析資料。 檢視自訂可以讓您篩選和排序資料，以尋找可能造成效能問題的函式。 「最忙碌路徑」篩選功能，則會在 [呼叫樹狀圖] 和 [模組] 檢視中提供您最活躍的路徑的即時反白顯示。

## <a name="modify-the-application-code"></a>修改應用程式程式碼
 在隔離出一個或多個相關效能問題後，您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE 修改程式碼，然後再收集變更的程式碼剖析資料。

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>再度收集分析資料並比較分析回合間的資料
 程式碼剖析工具的 [比較報告] 檢視顯示兩個選取的程式碼剖析資料檔間，在模組、函式或程式行方面的差異。 您可以指定要比較的程式碼剖析資料值，並可以在 [比較] 檢視和個別檔案檢視之間進行切換。

## <a name="generate-a-report-of-the-results"></a>產生結果報表
 您可以將任何效能報告檢視的資料列貼入電子郵件和試算表中，而且可以產生包含一個或多個檢視資料的報告。

## <a name="see-also"></a>另請參閱
- [概觀](../profiling/overviews-performance-tools.md)
- [逐步解說：找出效能問題](beginners-guide-to-cpu-sampling.md)
