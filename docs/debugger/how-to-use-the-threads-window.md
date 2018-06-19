---
title: 偵錯多執行緒應用程式
description: 偵錯使用 Visual Studio 中的 [執行緒] 視窗和偵錯位置工具列
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37a9161011031c53ed16a9ab0918eb498f5fa270
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926237"
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>逐步解說： 偵錯 Visual Studio 中使用 [執行緒] 視窗中的多執行緒應用程式
Visual Studio 提供**執行緒**視窗以及其他使用者介面來協助您偵錯多執行緒應用程式的項目。 本教學課程示範如何使用**執行緒**視窗和**偵錯位置**工具列。 如需其他工具的資訊，請參閱[開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)。 本教學課程只需要幾分鐘時間，但是完成它會讓您熟悉的偵錯多執行緒應用程式的功能。   
  
若要開始本教學課程，您需要的多執行緒應用程式專案。 請依照下列步驟建立專案。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>若要建立多執行緒應用程式專案  
  
1.  在**檔案**功能表上，選擇**新增**，然後按一下 **專案**。  
  
     [ **新增專案** ] 對話方塊隨即出現。  
  
2.  在**專案類型**s 方塊中，按一下您所選擇的語言： **Visual Basic**， **Visual C#**，或**Visual c + +**。  
  
3.  在**範本**方塊中，選擇**主控台應用程式**。  
  
4.  在**名稱**方塊中，輸入名稱 MyThreadWalkthroughApp。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     新的主控台專案隨即出現。 專案建立之後，便會出現原始程式檔 (Source File)。 根據您所選擇的語言，原始程式檔的名稱可能是 Module1.vb、Program.cs 或 MyThreadWalkthroughApp.cpp  
  
6.  刪除原始程式檔中出現的程式碼，會出現在 [建立執行緒] 區段，本主題的範例程式碼以取代[建立執行緒和開始時間傳遞資料](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time)。  
  
7.  在**檔案**功能表上，按一下 **全部儲存**。  
  
#### <a name="to-begin-the-tutorial"></a>若要開始本教學課程  
  
-   在原始碼程式碼編輯器中，尋找下列程式碼：  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine()
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>若要啟動偵錯  
  
1.  按一下左邊的裝訂邊的`Console.WriteLine`陳述式來插入新的中斷點。  
  
     在原始碼程式碼編輯器左側裝訂邊上，會出現一個紅色圓圈。 這表示這個位置現在已設定中斷點。  
  
2.  在**偵錯**功能表上，按一下 **開始偵錯**(**F5**)。  
  
     偵錯作業啟動，您的主控台應用程式 (Console Application) 開始執行，然後在中斷點停止。  
  
3.  如果目前焦點在主控台應用程式視窗上，請按一下 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 視窗將焦點還給 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
4.  在原始碼程式碼編輯器中，尋找包含下列程式碼的那一行：  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>若要尋找執行緒標記  

1.  在 [偵錯] 工具列上，按一下 **在來源中顯示執行緒**按鈕![在來源中顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。 
  
2.  查看來源視窗左邊的裝訂邊。 在這行中，您會看到*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")類似於兩條布條。 執行緒標記表示執行緒會停在這個位置上。  
  
3.  將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。 此案例中只有一個執行緒，其名稱可能為 `<noname>`。  

    > [!TIP]
    > 您可能會發現沒有名稱的執行緒識別透過重新命名，很有幫助。 在 執行緒 視窗中，選擇 **重新命名**之後上按一下滑鼠右鍵**名稱**執行緒資料列中的資料行。
  
4.  以滑鼠右鍵按一下執行緒標記，若要查看的捷徑功能表上的可用選項。 
    
  
## <a name="flagging-and-unflagging-threads"></a>將執行緒加上旗標和取消旗標  
您可以標示您要特別注意的執行緒。 加上旗標的執行緒是一個好的方法來追蹤重要的執行緒，並略過您不在意的執行緒。  
  
#### <a name="to-flag-threads"></a>若要為執行緒加上旗標   

1.  在**檢視**功能表上，指向**工具列**。  
  
    請確定**偵錯位置**工具列選取。

2.  移至**偵錯位置**工具列，並按一下**執行緒**清單。  
  
    > [!NOTE]
    >  您可以透過三個明顯的清單辨認出這個工具列：**程序**，**執行緒**，和**堆疊框架**。  
  
3.  注意清單中出現的執行緒數。  
  
4.  請回到原始碼程式碼編輯器，以滑鼠右鍵按一下執行緒標記![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")一次。  
  
5.  在捷徑功能表上指向**旗標**，然後按一下執行緒名稱和 ID 編號。  
  
6.  請返回**偵錯位置**工具列和尋找**僅顯示已標幟的執行緒**圖示![顯示已標幟執行緒](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")至右側**執行緒**清單。  
  
    在按鈕上的旗標圖示先前呈現暗。 現在，它是使用中的按鈕。  
  
7.  按一下**僅顯示已標幟的執行緒**圖示。  
  
    現在清單中只會出現加上旗標的執行緒。 (您可以按一下可切換回到單一旗標按鈕**顯示所有執行緒**模式。)

8. 開啟 [執行緒] 視窗中選擇**偵錯 > Windows > 執行緒**。

    ![執行緒視窗](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    在**執行緒**視窗中，加上旗標的執行緒都有附加的明顯的紅色旗標圖示。

    > [!TIP]
    > 當您有某些執行緒加上標幟時，您可以在程式碼編輯器的程式碼行上按一下滑鼠右鍵並選擇**執行至游標處加上旗標的執行緒**（請確定您選擇的所有已標幟的執行緒程式碼會到達）。 這將會暫停程式碼，讓您更容易控制所執行的順序選取行上的執行緒[凍結和解除凍結執行緒](#bkmk_freeze)。
  
11. 在來源的程式碼編輯器中，以滑鼠右鍵按一下執行緒標記一次。  
  
     請注意捷徑功能表上目前可用的選項。 而不是**旗標**，您現在會看到**取消旗標**。 不要在上面按一下**取消旗標**。  

     若要瞭解如何取消執行緒的旗標，請移至下一個程序。  
  
#### <a name="to-unflag-threads"></a>若要取消執行緒的旗標  
  
1.  在**執行緒**視窗中，以滑鼠右鍵按一下對應到已標幟執行緒的行。  
  
     捷徑功能表即會顯示。 它有選項可讓**取消旗標**和**取消旗標的所有執行緒**。  
  
2.  若要取消執行緒的旗標，按一下**取消旗標**。  

    查看**偵錯位置**工具列一次。 **僅顯示已標幟的執行緒**按鈕會呈暗灰色一次。 您已將唯一有旗標的執行緒取消旗標。 因為沒有已標幟的執行緒，工具列回到**顯示所有執行緒**模式。 按一下**執行緒**清單，並確認您可以看見所有執行緒。  
  
5.  請返回**執行緒**視窗及查看資訊欄。  
  
    在第一欄中，您會發現在執行緒清單的每個資料列的旗標外框圖示。 （外框表示這個執行緒已經未標示）。  
  
6.  按一下旗標外框的圖示兩個執行緒的第二個和第三個清單的底部。 

    旗標圖示會成為紅色，而非空心的外框。  
  
7.  按一下旗標欄位頂端的按鈕。  
  
    按一下這個按鈕，執行緒清單的順序就會變更。 執行緒清單現在的排序是將加上旗標的執行緒列於最上方。  
  
8.  再按一下旗標欄位頂端的按鈕。  
  
    排序順序會再次變更。  
  
## <a name="more-about-the-threads-window"></a>執行緒視窗的相關資訊  
  
#### <a name="to-learn-more-about-the-threads-window"></a>若要進一步了解執行緒視窗  
  
1.  在**執行緒**視窗中，檢查從左邊的第三個資料行。 在此資料行最上方的按鈕顯示**識別碼**。  
  
2.  按一下**識別碼**。  
  
     執行緒清單現在會依照執行緒 ID 編號排序。  
  
3.  以滑鼠右鍵按一下清單中任一個執行緒。 在捷徑功能表，按一下 **十六進位顯示**。  
  
     執行緒 ID 編號的格式即會變更。  
  
4.  將滑鼠指標停留**位置**資料行清單中的任何執行緒。  
  
     稍等一下，資料提示方塊就會出現。 它會顯示執行緒的部分呼叫堆疊。

     > [!TIP]
     > 執行緒的呼叫堆疊的圖形檢視，開啟[平行堆疊](../debugger/using-the-parallel-stacks-window.md)視窗 (偵錯時，選擇 **偵錯 / Windows / 平行堆疊**)。  
  
5.  查看第四個資料行，從左邊標示為**類別**。 執行緒已分到這些類別中。  
  
     處理序中第一個建立的執行緒稱為主執行緒。 請在執行緒清單中找出這個執行緒。  
  
6.  以滑鼠右鍵按一下主執行緒，然後按一下**切換至執行緒**。  
  
     A**中斷模式** 視窗隨即出現。 它會告訴您，偵錯工具目前並未執行 （因為它是主執行緒），它可以顯示的任何程式碼。   
  
7.  查看**呼叫堆疊**視窗和**偵錯位置**工具列。  
  
     內容**呼叫堆疊**視窗已變更。 

## <a name="bkmk_freeze"></a> 凍結和解除凍結執行緒的執行 

您可以凍結和解除凍結 （暫止和繼續） 控制執行緒執行工作順序的執行緒。 這可協助您解決並行存取問題，像是死結和競爭情形。

> [!TIP]
> 如果您想要在不凍結其他的執行緒 （也常見偵錯的狀況） 的情況下遵循單一執行緒，請參閱[開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread)。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>若要凍結和解除凍結執行緒  
  
1.  在**執行緒**視窗中，以滑鼠右鍵按一下任何執行緒，然後按一下**凍結**。  
  
2.  看看第二個資料行 （目前的執行緒資料行）。 暫停圖示現在會顯示那里。 這些暫停圖示表示已凍結執行緒。  
  
3.  顯示**暫停計數**資料行中選取它**資料行**清單。

    執行緒的暫停次數 (Suspend Count) 現在是 1。  
  
4.  以滑鼠右鍵按一下凍結的執行緒，然後按一下**解除凍結**。  
  
     目前的執行緒資料行和**暫停計數**資料行變更。 
  
## <a name="switching-the-to-another-thread"></a>切換至另一個執行緒 
  
#### <a name="to-switch-threads"></a>若要切換執行緒  
  
1.  在**執行緒**視窗中，檢查第二個資料行，從左 （目前的執行緒資料行）。 這個欄位頂端的按鈕沒有文字或圖示。
  
2.  查看目前的執行緒資料行，並注意其中一個執行緒具有黃色箭號。 黃色箭號表示這個執行緒是目前的執行緒 （這是執行指標的目前位置）。
  
    記下的執行緒 ID 編號，您會看到目前的執行緒圖示。 您會將目前的執行緒圖示移至另一個執行緒，但您必須將其放回當您完成。 
  
3.  另一個執行緒上按一下滑鼠右鍵，然後按一下 **切換至執行緒**。  
  
4.  查看**呼叫堆疊**原始程式碼編輯器 視窗。 內容已有所變更。  
  
5.  查看**偵錯位置**工具列。 目前的執行緒圖示已變更過。  
  
6.  移至**偵錯位置**工具列。 選取不同的執行緒從**執行緒**清單。  
  
7.  查看**執行緒**視窗。 目前的執行緒圖示已變更。  
  
8. 在來源的程式碼編輯器中，以滑鼠右鍵按一下執行緒標記。 在捷徑功能表上指向**切換至執行緒**按一下執行緒名稱 /ID 編號。  
  
     您現在已了解變更到另一個執行緒目前的執行緒圖示的三種方式： 使用**執行緒**視窗中，**執行緒**清單中**偵錯位置**工具列上，而在原始碼程式碼編輯器中的執行緒標記。  
  
     與執行緒標記，您只能切換到停止在該特定位置的執行緒。 使用**執行緒**視窗和**偵錯位置**工具列上，您可以切換至任何執行緒。   
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)
