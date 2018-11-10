---
title: 測試雲端服務的效能 |Microsoft Docs
description: 測試使用 Visual Studio 分析工具的雲端服務的效能
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001417"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>測試雲端服務的效能
## <a name="overview"></a>總覽
您可以透過下列方式測試雲端服務的效能：

* 使用 Azure 診斷，來收集資訊關於要求和連接，並檢閱顯示服務執行從客戶觀點來看的網站統計資料。 若要開始使用，請參閱[適用於 Azure 雲端服務和虛擬機器設定診斷](http://go.microsoft.com/fwlink/p/?LinkId=623009)。
* 您可以使用 Visual Studio 分析工具取得的服務執行情況在計算方面的深入分析。 如本主題所述，您可以使用程式碼剖析工具測量服務在 Azure 中執行。 如需如何使用程式碼剖析工具測量服務在本機執行於計算模擬器的資訊，請參閱[測試的 Azure 雲端服務在本機效能，在計算模擬器中使用 Visual Studio Profiler](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>選擇效能測試方法
### <a name="use-azure-diagnostics-to-collect"></a>您可以使用 Azure 診斷來收集：
* 網頁或服務，例如要求和連接的統計資料。
* 角色，例如角色重新啟動的頻率的統計資料。
* 整體的執行中角色設定記憶體使用量，例如記憶體回收行程所需時間的記憶體百分比的相關資訊。

### <a name="use-the-visual-studio-profiler-to"></a>使用 Visual Studio 分析工具：
* 判斷哪一個函式接受最多時間。
* 測量每一部分密集運算的程式花費多少時間。
* 比較兩個版本的服務的詳細的效能報告。
* 分析記憶體配置比個別的記憶體配置的層級的更多詳細資料。
* 分析多執行緒程式碼中的並行處理問題。

當您使用分析工具時，您可以在雲端服務執行時在本機或在 Azure 中收集資料。

### <a name="collect-profiling-data-locally-to"></a>本機收集分析資料來：
* 測試雲端服務的一部分的效能，例如特定的背景工作角色執行時，不需要實際模擬的負載。
* 受控制的情況下，隔離測試雲端服務的效能。
* 測試雲端服務的效能，再將它部署至 Azure。
* 不會干擾現有的部署，私下測試雲端服務的效能。
* 測試服務的效能，而不必支付費用，在 Azure 中執行。

### <a name="collect-profiling-data-in-azure-to"></a>在 Azure 中的程式碼剖析資料收集：
* 測試模擬或實際負載下的雲端服務的效能。
* 使用檢測方法收集分析資料，如本主題稍後所述。
* 在與生產環境中的服務執行時相同的環境中測試服務的效能。

您通常會模擬負載以測試雲端服務在標準模式或壓力狀況。

## <a name="profiling-a-cloud-service-in-azure"></a>分析在 Azure 中的雲端服務
當您發行您的雲端服務，從 Visual Studio 時，您可以分析服務，並指定為您想要的資訊提供您的程式碼剖析設定。 每個角色執行個體啟動分析工作階段。 如需如何從 Visual Studio 發行服務的詳細資訊，請參閱[從 Visual Studio 發佈至 Azure 雲端服務](https://msdn.microsoft.com/library/azure/ee460772.aspx)。

若要深入了解 Visual Studio 中的效能分析，請參閱[效能分析的初級開發人員指南](https://msdn.microsoft.com/library/azure/ms182372.aspx)並[使用程式碼剖析工具分析應用程式效能](https://msdn.microsoft.com/library/azure/z9z62c29.aspx)。

> [!NOTE]
> 您可以啟用 IntelliTrace 或程式碼剖析，當您發行雲端服務。 您不能同時啟用。
> 
> 

### <a name="profiler-collection-methods"></a>Profiler 收集方法
您可以使用不同的收集方法，以進行分析，根據您的效能問題：

* **CPU 取樣**-這個方法會收集對 CPU 使用率問題的初始分析有用的應用程式統計資料。 CPU 取樣是開始大多數效能調查的建議的方法。 收集 CPU 取樣資料時，您要分析的應用程式沒有影響很小。
* **檢測**-這個方法會收集對重點分析和輸入/輸出效能問題分析有用的詳細的計時資料。 檢測方法會記錄每個項目、 結束和函式呼叫的函式的模組中執行分析期間。 此方法可用來收集程式碼區段的詳細計時資訊，以及了解輸入和輸出作業對應用程式效能的影響。 執行 32 位元作業系統的電腦已停用這個方法。 只有在您的雲端服務在 Azure 中執行，不是在本機計算模擬器中時，才使用此選項。
* **.NET 記憶體配置**-這個方法會使用取樣分析方法來收集.NET Framework 記憶體配置資料。 收集的資料會包含已配置物件的大小與數量。
* **並行**-這個方法會收集資源爭用資料，並可用於分析多執行緒及多處理序應用程式的處理序和執行緒執行資料。 並行方法會收集每個封鎖執行程式碼之事件的資料，例如，執行緒等待釋放鎖定應用程式資源存取時。 此方法適用於分析多執行緒應用程式。
* 您也可以啟用**階層互動分析**，以提供有關執行時間的其他資訊的同步 ADO.NET 呼叫函式與一個或多個資料庫通訊的多層式應用程式中。 您可以使用任何程式碼剖析方法收集階層互動資料。 如需有關階層互動分析的詳細資訊，請參閱 <<c0> [ 階層互動檢視](https://msdn.microsoft.com/library/azure/dd557764.aspx)。

## <a name="configuring-profiling-settings"></a>設定分析設定
下圖顯示如何設定從 [發行 Azure 應用程式] 對話方塊中的程式碼剖析設定。

![進行程式碼剖析設定](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> 若要啟用**啟用程式碼剖析**核取方塊，您必須擁有用來發行您的雲端服務在本機電腦上安裝分析工具。 根據預設，當您安裝 Visual Studio 安裝程式碼剖析工具。
> 
> 

### <a name="to-configure-profiling-settings"></a>設定分析設定
1. 在 方案總管 中，開啟您的 Azure 專案的捷徑功能表，然後再選擇 **發佈**。 如需如何發佈雲端服務的詳細步驟，請參閱[發佈雲端服務使用的 Azure 工具](http://go.microsoft.com/fwlink/p?LinkId=623012)。
2. 在 **發佈 Azure 應用程式** 對話方塊中，選擇**進階設定** 索引標籤。
3. 若要啟用分析，請選取**啟用程式碼剖析**核取方塊。
4. 若要設定您的程式碼剖析設定，請選擇**設定**超連結。 [設定檔設定] 對話方塊隨即出現。
5. 從**您要使用何種方法的程式碼剖析**選項按鈕，選擇 程式碼剖析，您需要的類型。
6. 若要收集階層互動分析資料，請選取**啟用階層互動分析**核取方塊。
7. 若要儲存設定，請選擇**確定** 按鈕。
   
    當您發行此應用程式時，這些設定用來建立每個角色的程式碼剖析工作階段。

## <a name="viewing-profiling-reports"></a>檢視分析報告
程式碼剖析工作階段會建立您的雲端服務中角色的每個執行個體。 若要檢視每個工作階段從 Visual Studio 的分析報告，您可以檢視 [伺服器總管] 視窗，然後選擇 [Azure 運算] 節點，以選取的角色執行個體。 然後，如下圖所示，您可以檢視分析報告。

![檢視來自 Azure 的分析報告](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>若要檢視分析報告
1. 若要檢視 Visual Studio 伺服器總管 視窗，在功能表列上選擇  檢視中，伺服器總管。
2. 選擇 Azure 計算 節點，然後選擇 Azure 部署節點，當您從 Visual Studio 發佈您選取要分析的雲端服務。
3. 若要檢視執行個體的分析報告，在服務中選擇的角色，開啟特定執行個體的捷徑功能表，然後選擇**檢視分析報告**。
   
    隨即從 Azure 下載.vsp 檔這份報表，並下載狀態會出現在 Azure 活動記錄檔。 當下載完成時，分析報告會顯示的索引標籤中名為 Visual Studio 的編輯器<Role name> *<Instance Number>* <identifier>.vsp。 報表的摘要資料隨即出現。
4. 若要顯示不同的報表，檢視目前的檢視清單中，選擇您想要的檢視類型。 如需詳細資訊，請參閱 <<c0> [ 程式碼剖析工具報告檢視](https://msdn.microsoft.com/library/azure/bb385755.aspx)。

## <a name="next-steps"></a>後續步驟
[偵錯雲端服務](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[從 Visual Studio 發佈至 Azure 雲端服務](https://msdn.microsoft.com/library/azure/ee460772.aspx)

