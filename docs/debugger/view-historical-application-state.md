---
title: 檢視先前使用 IntelliTrace 的應用程式狀態
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d43e1a04570d68ce69f283cde264280fc24865a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846859"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>檢查先前使用 IntelliTrace 倒退，Visual Studio 中的應用程式狀態

IntelliTrace 回溯會自動擷取快照的應用程式在每個中斷點和偵錯工具逐步執行事件。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

IntelliTrace 回溯可從 Visual Studio Enterprise 2017 15.5 版和更高版本，而且需要 Windows 10 年度更新版或更新版本。 目前支援偵錯 ASP.NET、 WinForms、 WPF、 受管理的主控台應用程式，與受管理的類別庫的功能。 從 Visual Studio 2017 Enterprise 15.7 版開始，此功能也支援 ASP.NET Core 和.NET Core。 從 Visual Studio 2017 Enterprise 版 15.9 Preview 2 中，此功能也支援以 Windows 為目標的原生應用程式。 目前不支援偵錯 UWP 應用程式。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟用 Intellitrace 事件與快照集
> * 瀏覽使用回溯和步驟轉寄命令的事件
> * 檢視事件的快照集
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>啟用 IntelliTrace 事件與快照集模式 

1. 在 Visual Studio Enterprise 中開啟您的專案。

1. 開啟**工具** > **選項** > **IntelliTrace**設定，然後選取選項**IntelliTrace 事件與快照集**. 

    從 Visual Studio 2017 Enterprise 版 15.9 Preview 2 中，此選項是**IntelliTrace 快照集 （managed 與原生）**。 

    ![啟用 IntelliTrace 事件與快照集模式](../debugger/media/intellitrace-enable-snapshots.png "啟用 IntelliTrace 事件與快照集模式")

1. 如果您想要設定的例外狀況的檢視快照集的選項，選擇**IntelliTrace** > **進階**從**選項** 對話方塊。

    這些選項是從 Visual Studio 2017 Enterprise 15.7 版中推出。

    ![設定例外狀況的快照集的行為](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    當您啟用事件與快照集時，建立例外狀況的快照集也會啟用預設值。 您可以取消選取 停用例外狀況的快照集**例外狀況事件收集快照**。 啟用這項功能時，會建立快照集，未處理例外狀況。 處理的例外狀況，才會擲回例外狀況，而且如果它不是重新擲回先前擲回例外狀況，就會建立一個快照。 您可以設定的例外狀況的快照集數目上限，從下拉式清單中選取值。 最大值適用於每次您的應用程式進入中斷模式下 （例如，當您的應用程式叫用中斷點）。

    > [!NOTE]
    > 拍攝快照時，僅適用於例外狀況事件，IntelliTrace 記錄。 Managed 程式碼，您可以指定 IntelliTrace 記錄哪些事件，方法是選取**工具** > **選項** > **IntelliTrace 事件**。

1. 在專案中，設定一或多個中斷點，並開始偵錯 (按下**F5**)，或啟動偵錯逐步執行程式碼 (**F10**或是**F11**)。

    IntelliTrace 快照的每個偵錯工具步驟、 中斷點事件和處理的例外狀況事件的應用程式的程序。 這些事件會記錄在**事件**索引標籤中**診斷工具**視窗中的，搭配其他 IntelliTrace 事件。 若要開啟此視窗，選擇**偵錯** > **Windows** > **顯示診斷工具**。

    相機圖示旁邊的快照集可供使用的事件。 

    ![事件索引標籤上，使用快照集](../debugger/media/intellitrace-events-tab-with-snapshots.png "中斷點和步驟的快照集的事件 索引標籤")

    基於效能考量，當您逐步執行非常快速，不會採用快照集。 如果沒有相機圖示旁邊的步驟，請嘗試逐步執行速度變慢。

## <a name="navigate-and-view-snapshots"></a>瀏覽及檢視快照集

1. 使用事件之間瀏覽**逐步返回 （Alt + [）** 並**逐步前進 (Alt +])** 中偵錯 工具列按鈕。

    這些按鈕可巡覽出現在事件**事件**索引標籤中**Diagnostic Tools window**。 若要逐步返回或前進事件自動啟動[歷程偵錯](../debugger/historical-debugging.md)上選取的事件。

    ![向後和向前按鈕](../debugger/media/intellitrace-step-back-icons-description.png "逐步前進] 和 [逐步返回按鈕")

    當您步驟後，或前進時，Visual Studio 會進入歷程偵錯模式。 在此模式中，偵錯工具的內容切換到選取的事件記錄時的時間。 Visual Studio 也會將指標移到 [來源] 視窗中的程式碼相對應的行。 

    從這個檢視中，您可以檢查中的值**呼叫堆疊**，**區域變數**，**自動變數**，以及**監看式**windows。 您也可以以變數，以檢視資料提示方塊和執行中的運算式評估為留**Immediate**視窗。 您會看到的資料是從應用程式的程序所花費的時間在該點的快照集。

    因此，例如，如果您已叫用中斷點，並採取步驟 (**F10**)，則**逐步返回**按鈕會置於對應至中斷點的程式碼行的歷程記錄模式中的 Visual Studio。 

    ![啟用快照集事件的歷程記錄模式](../debugger/media/intellitrace-historical-mode-with-snapshot.png "啟用快照集事件的歷程記錄模式")

2. 若要返回即時執行，請選擇**繼續 (F5)** 或按**返回即時偵錯**資訊列中的連結。 

3. 您也可以檢視從快照集**事件** 索引標籤。若要這樣做，請選取具有快照集的事件，然後按一下**啟用歷程偵錯**。

    ![啟動 事件中的 歷程偵錯](../debugger/media/intellitrace-activate-historical-debugging.png "啟用歷程偵錯事件")

    不同於**設定下一個陳述式**命令，檢視快照集不會重新執行您的程式碼，它可讓您的應用程式狀態的靜態檢視表的某一點發生在過去的時間。

    ![IntelliTrace 回溯概觀](../debugger/media/intellitrace-step-back-overview.png "概觀的 IntelliTrace 回溯")

    若要深入了解如何檢查 Visual Studio 中的變數，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>常見問題集

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>有何 IntelliTrace 回溯 IntelliTrace 事件的唯一模式不同？

IntelliTrace 事件模式讓您啟動偵錯工具步驟及中斷點上的歷程偵錯。 不過，IntelliTrace 只會擷取中的資料**區域變數**並**自動變數**windows，如果 windows 已開啟，而且它只會擷取已展開的資料和檢視中。 事件模式，您通常沒有變數和複雜物件的完整檢視。 此外，運算式評估和檢視中的資料**監看式**視窗不支援。 

在事件與快照集模式中，IntelliTrace 會擷取整個快照集的應用程式的程序，包括複雜物件。 在一行程式碼中，您可以看到相同的資訊，如同您已在中斷點停止 （且不論是否之前展開過的資訊）。 檢視快照集時，也支援運算式評估。  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>什麼是這項功能的效能影響？ 

在逐步執行的整體效能的影響取決於您的應用程式。 建立快照集的額外負荷是大約 30 毫秒。 當建立快照時，應用程式的程序分叉部署和分支的複本已暫止。 當您檢視快照集時，會將 Visual Studio 附加至處理程序的分支複本。 每個快照集，Visual Studio 複製頁面資料表中，並將頁面設定為寫入時複製也一樣。 如果物件在堆積上的變更相關聯的快照集偵錯工具步驟之間，個別的頁面資料表會複製，導致最少的記憶體成本。 如果 Visual Studio 偵測到沒有足夠的記憶體來建立快照集，它不會其中一個。
 
## <a name="known-issues"></a>已知問題  
* 如果您的 Windows 10 Fall Creators Update (RS3)，比舊的 Windows 版本上使用 IntelliTrace 事件與快照集模式，而且應用程式的偵錯平台目標設定為 x86，IntelliTrace 不會快照集。

    因應措施︰
  * 如果您是在 Windows 10 年度更新 (RS1) 且 10.0.14393.2273，版本若低於[安裝 KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)。 
  * 如果您是在 Windows 10 Creators Update (RS2) 上且 10.0.15063.1112，版本若低於[安裝 KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722)。
  * 安裝或升級至 Windows 10 Fall Creators Update (RS3)。 
  * 或者： 
    1. 從 Visual Studio 安裝程式安裝適用於桌上型電腦 (x86、x64) 的 VC++ 2015.3 v140 工具組。
    2. 建置目標應用程式。
    3. 從命令列使用 editbin 工具設定`Largeaddressaware`目標可執行檔的旗標。 比方說，您可以使用此命令 （在之後更新的路徑）:"C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/Largeaddressaware"C:\Path\To\Application\app.exe"。
    4. 若要開始偵錯，請按 **F5**。 現在，在偵錯工具步驟及中斷點上建立快照集。

       > [!Note]
       > `Largeaddressaware`旗標必須設定每個可執行檔根據變更的時間。

* 當應用程式的程序的快照集後的應用程式，會使用持續性的記憶體對應檔案時，與快照集的程序保留獨佔鎖定記憶體對應檔案 （即使父處理序已釋放其鎖定）。 其他處理序都仍然能夠讀取，但不是寫入至記憶體對應檔案。

    因應措施：
    * 清除所有快照集結束偵錯工作階段。 

* 偵錯的處理程序有大量的唯一記憶體區域，例如載入大量的 Dll，應用程式的應用程式時可能會影響逐步效能，以啟用快照集。 在 Windows 的未來版本中，將會解決這個問題。 如果您遇到此問題，請透過歡迎來信stepback@microsoft.com。 

* 儲存的檔案時**偵錯 > IntelliTrace > 儲存 IntelliTrace 工作階段**在事件與快照集模式下，從快照集所擷取的其他資料中沒有.itrace 檔案。 中斷點和步驟的事件，您會看到相同的資訊，如同您已經在 IntelliTrace 事件的唯一模式下儲存檔案。 

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何使用 IntelliTrace 回溯。 若要深入了解其他 IntelliTrace 功能。

> [!div class="nextstepaction"]
> [IntelliTrace 功能](../debugger/intellitrace-features.md)
