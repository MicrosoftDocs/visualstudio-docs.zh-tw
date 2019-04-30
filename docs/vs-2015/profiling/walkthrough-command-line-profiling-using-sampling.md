---
title: 逐步解說：使用取樣進行命令列分析 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439689"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>逐步解說：命令列使用取樣分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說將示範如何使用命令列工具和取樣來剖析應用程式，以識別效能問題。  
  
 在這個逐步解說中，您將使用命令列工具來逐步剖析受管理的應用程式，並使用取樣以隔離並識別應用程式中的效能問題。  
  
 在這個逐步解說中，您將會依照下列步驟進行：  
  
- 使用命令列工具和取樣來剖析應用程式。  
  
- 分析取樣的分析結果，找出並修正效能問題。  
  
## <a name="prerequisites"></a>必要條件  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]或 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- 對 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] 有中等程度的了解  
  
- 對使用命令列工具有中等程度的了解  
  
- 一份 [PeopleTrax 範例](../profiling/peopletrax-sample-profiling-tools.md)  
  
- 若要處理剖析所提供的資訊，您手邊最好有偵錯符號資訊。  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>使用取樣方法進行命令列剖析  
 「取樣」是一種剖析的方法，會定期輪詢特定處理序以判斷使用中的函數。 產生的資料會提供計數，表示在取樣處理序時，函式位於呼叫堆疊頂端的頻率。  
  
> [!NOTE]
> 程式碼剖析工具的命令列工具位於 Visual Studio 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼分析工具命令列工具，必須將路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 PeopleTrax 是 32 位元應用程式。  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>使用取樣方法剖析 PeopleTrax 應用程式  
  
1. 安裝 PeopleTrax 範例應用程式，並建置該應用程式的「發行」版本。  
  
2. 開啟 [命令提示字元] 視窗，並將 [程式碼剖析工具] 目錄加入至本機的 Path 環境變數。  
  
3. 將工作目錄變更為包含 PeopleTrax 二進位檔的目錄。  
  
4. 輸入下列命令，以設定適當的環境變數：  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. 執行 VSPerfCmd.exe 這個控制分析工具的命令列工具，以開始剖析。 下列命令會以取樣模式啟動應用程式和分析工具：  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     分析工具處理序隨即開始，並附加至 PeopleTrax.exe 處理序。 分析工具處理序開始將收集到的剖析資料寫入報告檔。  
  
6. 按一下 [取得人員]。  
  
7. 按一下 [匯出資料]。  
  
     [記事本] 便會開啟，並顯示包含從 [PeopleTrax] 匯出之資料的新檔案。  
  
8. 關閉 [記事本]，然後關閉 **PeopleTrax** 應用程式。  
  
9. 關閉分析工具。 輸入下列命令：  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. 使用下列命令，以重設環境變數：  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. 剖析資料會儲存在 .vsp 檔案中，請使用下列其中一個方法來分析結果：  
  
    - 在 Visual Studio IDE 中開啟 .vsp 檔案。  
  
         — 或 —  
  
    - 使用 VSPerfReport.exe 命令列工具產生逗號分隔值 (.csv) 檔案。 若要產生報表以供在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 外部使用，請使用下列命令：  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>另請參閱  
 [效能工作階段概觀](../profiling/performance-session-overview.md)   
 [從命令列使用程式碼剖析工具](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [了解取樣資料值](../profiling/understanding-sampling-data-values.md)   
 [效能報告檢視](../profiling/performance-report-views.md)
