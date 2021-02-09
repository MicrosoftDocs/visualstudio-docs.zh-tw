---
title: 使用 IntelliTrace 檢視先前的應用程式狀態
description: 了解如何建立快照集，以及使用 IntelliTrace 回溯檢視快照集
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1ab54ccb3820b3a03724c30d16f08b3e8a45493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933098"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>使用 Visual Studio 中的 IntelliTrace 回溯，檢查先前的應用程式狀態 (Visual Studio Enterprise)

IntelliTrace 回溯會自動擷取應用程式在每個中斷點以及偵錯工具步驟事件的快照。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

IntelliTrace 回溯可用於 Visual Studio Enterprise 2017 15.5 版和更新版本，而且需要 Windows 10 年度更新版或更新版本。 目前的功能支援對 ASP.NET、WinForms、WPF、受控主控台應用程式和與受控類別庫進行偵錯。 從 Visual Studio 2017 Enterprise 15.7 版開始，此功能也支援 ASP.NET Core 和 .NET Core。 從 Visual Studio 2017 Enterprise 15.9 Preview 2 版開始，此功能也支援以 Windows 為目標的原生應用程式。 目前不支援對 UWP 應用程式進行偵錯。

在本教學課程中，您將：

> [!div class="checklist"]
> * 啟用 IntelliTrace 事件與快照集
> * 使用回溯和快轉命令來巡覽事件
> * 檢視事件快照

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>啟用 Intellitrace 事件與快照模式

1. 在 Visual Studio Enterprise 中開啟您的專案。

1. 開啟 [**工具**  >  **選項**  >  **intellitrace** 設定]，然後選取 [ **intellitrace 事件和快照**] 選項。

    從 Visual Studio 2017 Enterprise 15.9 Preview 2 版開始，此選項是 [IntelliTrace 快照 (受控與原生)]。

    ![啟用 IntelliTrace 事件與快照模式](../debugger/media/intellitrace-enable-snapshots.png "啟用 IntelliTrace 事件與快照模式")

1. 如果您想要設定選項來查看例外狀況的快照集，請  >  從 [**選項**] 對話方塊中選擇 [IntelliTrace **Advanced** ]。

    這些選項從 Visual Studio 2017 Enterprise 15.7 版開始提供。

    ![在例外狀況設定快照的行為](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    當您啟用事件與快照時，根據預設也會啟用在例外狀況建立快照。 您可以取消選取 [在例外狀況事件收集快照] 來停用例外狀況上的快照。 啟用這項功能時，會為未處理的例外狀況建立快照。 針對已處理的例外狀況，僅會在擲回例外狀況且不重新擲回先前擲回的例外狀況時，才會建立快照。 您可以透過從下拉式清單中選取值，來設定例外狀況的最大快照數。 每次應用程式進入中斷模式時 (例如當您的應用程式遇到中斷點時)，會套用最大值。

    > [!NOTE]
    > 僅會對 IntelliTrace 記錄的例外狀況事件建立快照。 針對 managed 程式碼，您可以選取 [**工具**  >  **選項**  >  **intellitrace 事件**] 來指定 intellitrace 記錄的事件。

1. 在專案中設定一或多個中斷點，並開始偵錯 (按下 **F5**)，或藉由逐步執行程式碼 (**F10** 或 **F11**) 開始偵錯。

    IntelliTrace 會在每個偵錯工具步驟、中斷點事件和未處理的例外狀況事件上，建立應用程式程序的快照。 這些事件會與其他 IntelliTrace 事件一起記錄在 [診斷工具] 視窗的 [事件] 索引標籤中。 若要開啟此視窗，請選擇 [ **Debug**  >  **Windows**  >  **Show 診斷工具**]。

    快照可供使用的事件旁會顯示相機圖示。

    ![具有快照的事件索引標籤](../debugger/media/intellitrace-events-tab-with-snapshots.png "中斷點上具有快照集和步驟的 [事件] 索引標籤")

    基於效能考量，當您快速逐步執行時，不會建立快照。 如果步驟旁沒有出現相機圖示，請嘗試放慢步驟。

## <a name="navigate-and-view-snapshots"></a>巡覽及檢視快照

1. 您可以使用偵錯工具列的 [回溯] 和 [快轉] 按鈕，在事件之間巡覽。

    這些按鈕會流覽 **診斷工具視窗** 的 [**事件**] 索引標籤中出現的事件。 回溯或前進至事件時，會自動啟動所選事件的歷程 [記錄調試](../debugger/historical-debugging.md) 程式。

    ![逐步執行和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png "逐步執行和向前前進按鈕")

    當您回溯或快轉時，Visual Studio 會進入歷程偵錯模式。 在此模式中，偵錯工具內容會切換到記錄所選事件時的當時間。 Visual Studio 也會將指標移到來源視窗中對應的程式碼行。

    在此檢視中，您可以檢查 [呼叫堆疊]、[本機]、[自動]和 [監看] 視窗中的值。 您也可以將游標暫留在變數上以檢視資料提示，並在 [立即] 視窗中執行運算式評估。 您所看到資料來自該時間點應用程式程序的快照。

    因此；例如，如果您遇到了中斷點並採取步驟了逐步執行 (**F10**)，則 [回溯] 按鈕會將 Visual Studio 置於歷程模式中與中斷點對應的程式碼行。

    ![在具有快照集的事件上啟用歷程記錄模式](../debugger/media/intellitrace-historical-mode-with-snapshot.png "在具有快照集的事件上啟用歷程記錄模式")

2. 若要返回即時執行，請選擇 [繼續 (F5)] 或按一下資訊列中的 [返回即時偵錯] 連結。

3. 您也可以從 [ **事件** ] 索引標籤查看快照集。若要這樣做，請選取具有快照集的事件，然後按一下 [ **啟用歷程記錄**]。

    ![啟用事件的歷程記錄偵錯工具](../debugger/media/intellitrace-activate-historical-debugging.png "啟用事件的歷程記錄偵錯工具")

    與 **Set Next Statement** 命令不同，檢視快照不會重新執行您的程式碼，而會為您提供過去發生的應用程式狀態靜態檢視。

    ![IntelliTrace 回溯簡介](../debugger/media/intellitrace-step-back-overview.png "IntelliTrace 回溯簡介")

    若要深入了解如何檢查 Visual Studio 中的變數，請參閱[偵錯工具簡介](../debugger/debugger-feature-tour.md)

## <a name="frequently-asked-questions"></a>常見問題集

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace 回溯與 IntelliTrace 事件唯一模式有何不同？

事件唯一模式下的 IntelliTrace，可讓您啟用偵錯工具步驟和中斷點上的歷程偵錯。 但是，如果視窗已開啟，則 IntelliTrace 只會擷取 [本機] 和 [自動] 視窗中的資料，並且只會擷取已展開且在檢視中的資料。 在事件唯一模式中，您通常沒有變數和複雜物件的完整檢視。 此外，不支援 [監看] 視窗中的運算式評估和檢視資料。

在事件與快照模式中，IntelliTrace 會擷取整個應用程式程序的快照，包括複雜物件。 在一行程式碼中，您可以看到與在中斷點停止時相同的資訊 (無論您先前是否展開過資訊)。 檢視快照時，也支援運算式評估。  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>這項功能對效能有何影響？ 

對整體逐步執行效能的影響，取決於您的應用程式。 建立快照的額外負荷大約是 30 毫秒。 建立快照時，應用程式的程序將會分支，並且分支的複本將會暫止。 當您檢視快照時，Visual Studio 附加至該程序的分支複本。 針對每個快照，Visual Studio 僅會複製頁面資料表，並將頁面設定為寫入時複製。 如果堆積上的物件在偵錯工具步驟與相關聯快照之間發生變更，則會複製對應的頁面資料表，進而最大限度降低記憶體成本。 如果 Visual Studio 偵測到沒有足夠的記憶體來擷取快照，則不會進行擷取。

## <a name="known-issues"></a>已知問題
* 如果在早於 Windows 10 Fall Creators Update (RS3) 的 Windows 版本上使用IntelliTrace 事件和快照模式，且如果應用程式的偵錯平台目標設定為 x86，則 IntelliTrace 不會建立快照。

    因應措施：
  * 如果您使用的是 Windows 10 年度更新 (RS1) 並低於 10.0.14393.2273 版，請[安裝 KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)。
  * 如果您使用的是 Windows 10 Creators Update (RS2) 並低於 10.0.15063.1112 版，請[安裝 KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722)。
  * 安裝或升級至 Windows 10 Fall Creators Update (RS3)。
  * 或者：
    1. 從 Visual Studio 安裝程式安裝適用於桌上型電腦 (x86、x64) 的 VC++ 2015.3 v140 工具組。
    2. 建置目標應用程式。
    3. 從命令列使用 editbin 工具來設定目標可執行檔的 `Largeaddressaware` 旗標。 例如，您可以使用此命令 (在更新路徑之後)："C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe"。
    4. 若要開始偵錯，請按 **F5**。 現在，系統會在偵錯工具步驟及中斷點上擷取快照。

       > [!Note]
       > 每次重建的可執行文件若有變更，都必須設定 `Largeaddressaware` 旗標。

* 當在使用持續性記憶體對應檔案的應用程式上建立應用程式程序快照時，具有快照的程序會在記憶體對應檔案上保持獨佔鎖定 (即使在父程序已解除其鎖定之後)。 其他程序仍然能夠讀取，但不能寫入記憶體對應檔案。

  因應措施：
  * 藉由結束偵錯工作階段來清除所有快照。

* 對其程序具有大量唯一記憶體區域的應用程式 (例如載入大量 DLL 的應用程式) 進行偵錯時，啟用快照的逐步執行效能可能會受到影響。 在未來的 Windows 版本中將會解決這個問題。 如果您遇到此問題，請透過 stepback@microsoft.com 與我們連絡。

* 在事件和快照模式下透過 [偵錯] > [IntelliTrace] > [儲存 IntelliTrace 工作階段] 儲存檔案時，無法從 .itrace 檔案中取得從快照擷取的其他資料。 在中斷點和步驟事件中，您會看到與在 IntelliTrace 事件唯一模式中儲存檔案相同的資訊。

## <a name="next-steps"></a>下一步

在本教學課程中，您已了解如何使用 IntelliTrace 回溯。 建議您深入了解其他 IntelliTrace 功能。

> [!div class="nextstepaction"]
> [IntelliTrace 功能](../debugger/intellitrace-features.md)
