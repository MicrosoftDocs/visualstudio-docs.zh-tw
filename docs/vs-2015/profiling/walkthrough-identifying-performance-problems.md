---
title: 逐步解說：找出效能問題 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0ac9d085a837ab3ab05754ce70d853112bc48d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096513"
---
# <a name="walkthrough-identifying-performance-problems"></a>逐步解說：找出效能問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說將示範如何剖析應用程式以找出效能問題。  
  
 在這個逐步解說中，您會逐步分析受管理的應用程式，並使用取樣和檢測來隔離並識別應用程式中的效能問題。  
  
 在這個逐步解說中，您將會依照下列步驟進行：  
  
- 使用取樣方法剖析應用程式。  
  
- 分析取樣的剖析結果，找出並修正效能問題。  
  
- 使用檢測方法剖析應用程式。  
  
- 分析檢測的剖析結果，找出並修正效能問題。  
  
## <a name="prerequisites"></a>必要條件  
  
- 對 C# 有中等程度的了解。  
  
- 一份 [PeopleTrax 範例](../profiling/peopletrax-sample-profiling-tools.md)。  
  
  若要處理剖析所提供的資訊，您手邊最好有偵錯符號資訊。  
  
## <a name="profiling-by-using-the-sampling-method"></a>使用取樣方法進行剖析  
 取樣是一種剖析的方法，會定期輪詢有問題的處理序以判斷使用中的函式。 產生的資料會提供計數，表示在取樣處理序時，有問題的函式位於呼叫堆疊頂端的頻率。  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>使用取樣方法剖析應用程式  
  
1. 以系統管理員權限開啟 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]。 需要以系統管理員身分執行剖析。  
  
2. 開啟 PeopleTrax 方案。  
  
     PeopleTrax 方案會填入 [方案總管] 中。  
  
3. 請將專案組態設定為 [發行]。  
  
     您應該使用發行組建來偵測應用程式中的效能問題。 由於偵錯組建編譯時會插入額外資訊，可能對效能產生負面影響，而無法正確描述效能問題，因此建議您在剖析時使用發行組建。  
  
4. 按一下 [分析]  功能表上的 [啟動效能精靈] 。  
  
     [效能精靈] 隨即出現。  
  
5. 確定已選取 [CPU 取樣 (建議使用)]，然後按 [下一步]。  
  
6. 在 [您要以哪一個應用程式做為剖析的目標] 中，選取 [PeopleTrax]，然後按 [下一步]。  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 會建置專案並開始剖析應用程式。 [PeopleTrax] 應用程式視窗隨即出現。  
  
7. 按一下 [取得人員]。  
  
8. 按一下 [匯出資料]。  
  
     [記事本] 便會開啟，並顯示包含從 [PeopleTrax] 匯出之資料的新檔案。  
  
9. 關閉 [記事本]，然後關閉 [PeopleTrax] 應用程式。  
  
     分析工具會產生程式碼剖析資料 (\*.vsp) 檔案，在 [效能總管] 視窗的 [報表] 區段中列出檔案名稱，並且在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 主視窗中自動載入資料檔案的 [摘要] 檢視。  
  
#### <a name="to-analyze-sampled-profiling-results"></a>分析取樣的剖析結果  
  
1. [摘要] 檢視會顯示在執行程式碼剖析過程中的 CPU 使用率時間軸、代表應用程式呼叫樹狀圖中最活躍分支的 [最忙碌路徑] 清單，以及執行函式主體中的程式碼時取得最多樣本之函式的 [執行最多個別工作的函式] 清單。  
  
     檢查 [最忙碌路徑] 清單，並且注意到 PeopleNS.People.GetNames 方法是最接近清單結尾的 PeopleTrax 函式。 這個位置讓它成為分析的候選項。 按一下函式名稱，在 [函式詳細資料] 檢視中顯示 GetNames 的詳細資料。  
  
2. [函式詳細資料] 檢視包含兩個視窗。 [成本分配] 視窗提供下列項目的圖形檢視：函式已完成的工作、它呼叫的函式已完成的工作，以及呼叫此函式之函式對取樣執行個體數目的比重。 您可以按一下函式名稱以變更檢視的焦點函式。 例如，您可以按一下 PeopleNS.People.GetPeople，讓 GetPeople 成為選取的函式。  
  
     [函式程式碼檢視] 視窗會顯示函式函式原始程式碼 (若可用)，並且反白顯示選取的函式中耗費最多資源的程式行。 選取 GetNames 時，您可以看到這個函式會從應用程式資源讀取字串，然後使用 <xref:System.IO.StringReader> 將字串中的每一行新增至 <xref:System.Collections.ArrayList>。 沒有顯著方式可以最佳化這個函式。  
  
3. 因為 PeopleNS.People.GetPeople 是 GetNames 的唯一呼叫端，請按一下 [成本分配] 視窗中的 [GetPeople] 來檢查其程式碼。 這個方法會從 GetNames 所產生的人員和公司名稱傳回 PersonInformationNS.PersonInformation 物件的 <xref:System.Collections.ArrayList>。 不過，每次建立 PersonInformation 物件時會呼叫 GetNames 兩次。 您會發現只要在方法開頭建立清單一次，然後在 PersonInformation 建立迴圈期間在這些清單中索引，即可輕鬆最佳化方法。  
  
4. 在範例應用程式的程式碼中提供了 GetPeople 替代版本，您可以將條件式編譯符號加入至組建屬性來呼叫最佳化函式。 在 [方案總管] 視窗中，以滑鼠右鍵按一下 [人員] 專案，然後按一下 [屬性]。 按一下屬性頁功能表上的 [建置]，然後在 [條件式編譯的符號] 文字方塊中輸入 **OPTIMIZED_GETPEOPLE**。 GetPeople 的最佳化版本就會在下一個組建中取代原始方法。  
  
5. 重新執行效能工作階段。 在 [效能總管] 工具列上，按一下 [啟動並啟用程式碼剖析]。 按一下 [取得人員]，然後按一下 [匯出資料]。 關閉出現的 [記事本] 視窗，然後關閉 PeopleTrax 應用程式。  
  
     隨即產生新的程式碼剖析資料檔案，而且新資料的 [摘要] 檢視會出現在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 主視窗中。  
  
6. 若要比較兩個程式碼剖析回合，請在 [效能總管] 中選取兩個資料檔案，以滑鼠右鍵按一下檔案，然後按一下 [比較效能報告]。 [比較報告] 視窗隨即出現在 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 主視窗中。 [差異] 資料行會顯示函式效能值從先前 [基準] 值到後來 [比較] 值的變更。 您可以在 [資料行] 下拉式清單中選取要比較的值。 選取 [內含樣本 %]。  
  
     您會發現 GetPeople 和 GetNames 方法的效能有顯著改進。  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>使用檢測方法進行剖析  
 「檢測」是一種剖析方法，分析工具會在受檢測二進位檔的特殊建置版本中插入探查函式。 探查會在檢測模組中收集函式進入和離開的時間資訊，以及這些函式內所有呼叫位置的時間資訊。 對於調查輸入/輸出作業相關問題 (如寫入磁碟和網路通訊)，檢測程序很有用。 檢測比取樣提供更詳細的資訊，但在程序執行上更具侵入性並且發生更大量的額外負荷。 已檢測之二進位檔的大小也會比偵錯或發行的二進位檔來得大，所以並不適合用來部署。  
  
 在本節的逐步解說中，我們將使用檢測方法來探索先前剖析的 PeopleTrax 應用程式中可以最佳化的其他程式碼。 透過使用 [摘要] 檢視時間表的篩選，我們將集中分析在進行程式碼剖析的應用程式中，將人員清單寫入 [記事本] 檔案的匯出資料案例。  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>使用檢測方法剖析現有的應用程式  
  
1. 必要時，在 Visual Studio 中開啟 PeopleTrax 應用程式。  
  
     確定您是以系統管理員身分執行，而且方案的組建組態已設為 [發行]。  
  
2. 在 [效能總管] 中，按一下 [檢測]。  
  
3. 在 [效能總管] 工具列上，按一下 [啟動並啟用程式碼剖析]。  
  
     分析工具就會建置專案並開始剖析應用程式。 [PeopleTrax] 應用程式視窗隨即出現。  
  
4. 按一下 [取得人員]。  
  
     PeopleTrax 資料格會填入資料。  
  
5. 等候約 10 秒，然後按一下 [匯出資料]。  
  
     [記事本] 便會啟動並顯示新檔案，這個新檔案則包含從 [PeopleTrax] 匯出的人員清單。 等候可讓您更輕鬆識別要篩選的資料匯出程序。  
  
6. 關閉 [記事本]，然後關閉 [PeopleTrax] 應用程式。  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 便會產生一份效能工作階段報告 (*.vsp)。  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>分析檢測的剖析結果  
  
1. 報表的 [摘要] 檢視中的時間表圖形會顯示在執行程式碼剖析期間程式的 CPU 使用率。 匯出資料作業應該是圖形右側的明顯尖峰或上升後的穩定階段。 我們可以篩選效能工作階段，只顯示及分析匯出作業中所收集的資料。 在圖形上，按一下匯出資料作業開始之時間點的左側。 再按一下作業的右側。 然後按一下時間表右側連結清單中的 [依選取範圍篩選]。  
  
    [最忙碌路徑] 樹狀圖顯示 PeopleTrax.Form1.ExportData 方法呼叫的 <xref:System.String.Concat%2A> 方法耗用大部分的時間。 因為 **System.String.Concat** 也是位於 [含有最多個別工作的函式] 清單的最上方，所以減少此函式所花費的時間是可能的最佳化方式。  
  
2. 在任一個摘要資料表中按兩下 [System.String.Concat]，查看 [函式詳細資料] 檢視中的詳細資訊。  
  
3. 您會發現 PeopleTrax.Form1.ExportData 是呼叫 Concat 的唯一方法。 按一下 [呼叫函式] 清單中的 [PeopleTrax.Form1.ExportData]，選取此方法做為 [函式詳細資料] 檢視的目標。  
  
4. 檢查 [函式程式碼檢視] 視窗中的方法。 請注意，並沒有 **System.String.Concat** 的常值呼叫。 相反地，有數個地方使用 += 運算元，編譯器將其取代為 **System.String.Concat** 的呼叫。 在 .NET Framework 中對一個字串所做的任何修改，都會導致一個新字串受到配置。 .NET Framework 含有 <xref:System.Text.StringBuilder> 類別，此類別會針對字串的串連進行最佳化  
  
5. 若要以最佳化的程式碼取代這個有問題的區域，請將 OPTIMIZED_EXPORTDATA 以條件式編譯符號的方式加入至 PeopleTrax 專案。  
  
6. 在 [方案總管] 中，以滑鼠右鍵按一下 [PeopleTrax] 專案，然後按一下 [屬性]。  
  
    [PeopleTrax] 專案屬性表單隨即出現。  
  
7. 按一下 [建置] 索引標籤。  
  
8. 在 [條件式編譯的符號] 文字方塊中，輸入 **OPTIMIZED_EXPORTDATA**。  
  
9. 關閉專案屬性表單，並在提示時選擇 [全部儲存]。  
  
   當您再次執行應用程式時，便可見到顯著的效能改進。 雖然使用者能感覺到效能已有所改善，還是建議您再次執行剖析工作階段。 由於第一個問題可能會遮蔽其他問題，因此在修正問題後再次檢閱資料是很重要的。  
  
## <a name="see-also"></a>另請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [入門](../profiling/getting-started-with-performance-tools.md)   
 [/Z7、/Zi、/ZI (偵錯資訊格式)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)
