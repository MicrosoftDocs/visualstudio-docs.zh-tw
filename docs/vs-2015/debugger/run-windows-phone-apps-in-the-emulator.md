---
title: 在模擬器中執行 Windows Phone 應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683530"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>在模擬器中執行 Windows Phone 應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Phone 模擬器提供一個虛擬化環境，在此環境中，就算沒有實體裝置，您還是可以在電腦上偵錯和測試 Windows Phone 應用程式。 您可以模擬常見觸控和旋轉事件，以及選擇您要模擬的實體螢幕大小和解析度。 您也可以測試許多常用功能，例如位置、網路、通知、感應器、加速計和選擇性的 SD 記憶卡。  
  
 如需您可以在模擬器中測試之功能的詳細資訊，請參閱 [Windows Phone 模擬器中的測試應用程式功能](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1)。  
  
 模擬器與 Visual Studio 搭配使用，能提供讓您用來設計、開發、偵錯和測試 Windows Phone 應用程式的完整環境。  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> 在模擬器中執行 Windows Phone 應用程式  
 雖然您正在開發 Windows Phone 應用程式，但是您可以使用 Windows Phone 模擬器快速部署和測試您的應用程式。 不過，建議您先在實際 Windows Phone 裝置上測試應用程式，再將應用程式發行至 Windows Phone 市集。 這樣可讓您以使用者的身分體驗您的應用程式。  
  
 第一次在 Windows Phone 模擬器中執行 Windows Phone 應用程式時，會發生下列事件：  
  
1. 模擬器啟動。  
  
2. 模擬器載入 Windows Phone 作業系統。  
  
3. 模擬器顯示 Windows Phone [開始] 畫面。  
  
4. 將您的應用程式部署至模擬器。  
  
5. 您的應用程式在模擬器上執行。  
  
   如果選取的模擬器已在執行，則會在執行中的模擬器內部署並啟動您的應用程式。 一次只能執行一個模擬器執行個體。  
  
> [!TIP]
> 在模擬器上測試應用程式時，請在偵錯工作階段之間開啟模擬器，以快速重新執行應用程式。  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> 從 Visual Studio 執行應用程式  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>從 Visual Studio 部署和執行應用程式  
  
1. 在 Visual Studio 中，開啟 Windows Phone 專案。  
  
2. 在 [ **標準** ] 工具列上，選取其中一個模擬器選項。  
  
     ![Windows Phone 模擬器影像清單](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. 若要使用偵錯工具來部署及執行應用程式，請在 [ **調試** 程式] 功能表上，按一下 [ **開始調試**程式]，或按 F5。  
  
     若要部署及執行您的應用程式而不進行偵錯工具，請在 [ **調試** 程式] 功能表上，按一下 [ **啟動但不**偵測]，或按 Ctrl  
  
     隨即會部署和啟動您的應用程式。  
  
     若要在不執行的情況下部署應用程式，請在 [ **組建** ] 功能表上，按一下 [ **部署方案**]。  
  
##### <a name="to-stop-a-running-app"></a>停止執行中的應用程式  
  
- 若要停止執行中的應用程式，請執行下列其中一項：  
  
  - 在 Visual Studio 的 [ **調試** ] 功能表上，按一下 [ **停止調試**]，或按 Shift + F5。  
  
  - 在模擬器中，按 [ **上一步** ] 按鈕結束應用程式。 如果應用程式的使用中頁面不是應用程式的起始頁，您可能必須多次按 [ **上一步** ] 按鈕。  
  
    應用程式即會結束，並開啟 [開始] 畫面。 這樣會結束目前的偵錯工作階段。  
  
##### <a name="to-restart-an-app-without-debugging"></a>重新啟動應用程式，而不進行偵錯  
  
1. 在模擬器中，於 [開始] 畫面上，往左撥動以檢視應用程式清單。  
  
2. 在應用程式清單中，點選應用程式圖示。 應用程式即會重新啟動，而不進行偵錯。  
  
##### <a name="to-deactivate-a-running-app"></a>停用執行中應用程式  
  
1. 執行應用程式之前，請在 Visual Studio 中，以滑鼠右鍵按一下方案總管中的專案，然後選取 [ **屬性** ] 以開啟 [ **專案設計**工具]。  
  
2. 在 [ **專案設計**工具] 的 [ **調試** 程式] 頁面上，如果您想要讓應用程式在停用時進入休眠狀態，請在 [ **偵錯工具停用時** 保留標記] 核取方塊。 如果您想要在停用時為應用程式加上標記，請核取此核取方塊。  
  
3. 在 [ **調試** 程式] 功能表上，按一下 [ **開始調試**程式]，或按 F5 執行應用程式。  
  
4. 在模擬器中，按下 [ **開始** ] 按鈕。 [開始] 畫面即會出現，並停用應用程式。 應用程式會進入休眠狀態或將其標記為已進行標記，這取決於 [在 **偵錯工具停用時** 標記] 核取方塊的設定。  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>重新啟用休眠或加上標記的應用程式  
  
- 在模擬器中，按 [ **上一步** ] 按鈕以返回應用程式。 如果您流覽至其他頁面，或已開啟另一個應用程式，您可能必須多次按 [ **上一步** ] 按鈕，才能重新啟用應用程式。  
  
     偵錯工作階段即會繼續。 如果偵錯工具已中斷與應用程式的連結，則可能需要按 F5 繼續偵錯工作階段。  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> 使用應用程式部署工具執行應用程式  
 您也可以使用 Windows Phone 應用程式部署工具 (**AppDeploy.exe**) 在模擬器中執行您的應用程式。 此工具是一個獨立應用程式，可在安裝 Windows Phone 開發工具時一併安裝。  
  
 如需詳細資訊，請參閱 [使用應用程式部署工具部署 Windows Phone 8.1 應用](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6)程式。  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> 使用模擬器工具列設定 Windows Phone 模擬器  
 下表顯示模擬器工具列上所提供的設定按鈕。  
  
|工具列按鈕|設定選項|  
|---------------------|---------------------------|  
|![Windows Phone 模擬器工具列上的輸入選項](../debugger/media/wp-emulator.png "WP_Emulator_")|**設定單點或多點輸入**<br /><br /> 當您啟用多點輸入時，可以按一下滑鼠右鍵移動觸控點，而不需觸控螢幕。 接著，您可以按滑鼠左鍵同時移動兩個觸控點。|  
|![Windows Phone 模擬器工具列上的方向](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**設定模擬器方向**<br /><br /> 您可以將 Windows Phone 模擬器中的方向變更為其中一個方向 (共三個方向)：直向、橫向 (左) 或橫向 (右)。 當您變更方向時，模擬器的大小並不會變更。<br /><br /> 若要變更方向，請按一下 [ **向左旋轉** ] 按鈕或 [向 **右** 旋轉] 按鈕。|  
|![Windows Phone 模擬器工具列上的大小選項](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**設定模擬器大小**<br /><br /> 您可以在主機電腦畫面上變更模擬器大小。 模擬器的 DPI 是根據主機監視器 DPI (不論縮放值為何)。<br /><br /> -若要讓模擬器符合螢幕，請按一下 [ **符合螢幕大小** ] 按鈕。<br />-若要變更縮放設定，請按一下 [ **縮放** ] 按鈕。 [ **縮放** ] 對話方塊隨即開啟。 在 [ **縮放** ] 對話方塊中，輸入介於33到100之間的縮放值。|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> 使用模擬器上的模擬硬體按鈕  
 使用模擬器螢幕右側的模擬硬體按鈕，以模擬電話硬體按鈕的使用。  
  
- 按一下 [ **電源** ] 按鈕可模擬關閉和開啟顯示器。 按住可模擬關閉電話。  
  
- 按一下 [ **音量向上** 或 **向下音量** ] 按鈕，以模擬變更電話說話者的電話和通知音量。  
  
- [ **相機** ] 按鈕會啟動相機應用程式。 您可以使用相機應用程式中的控制項，模擬照相或拍攝影片。  
  
  下列螢幕擷取畫面顯示模擬的硬體按鈕。  
  
1. 左側影像顯示模擬器上的 [開始] 畫面。  
  
2. 中間影像會在按 [ **電源** ] 按鈕關閉顯示器之後顯示模擬器。  
  
3. 右側影像會在按下 **音量** 按鈕來增加磁片區之後，顯示模擬器畫面。  
  
   ![Windows Phone 模擬器上的按鈕](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> 搭配使用電腦鍵盤與模擬器  
 模擬器支援將您開發電腦上的硬體鍵盤對應至 Windows Phone 上的鍵盤。 按鍵的行為與 Windows Phone 裝置上相同。  
  
 預設不會啟用硬體鍵盤。 這項實作等同於使用硬體鍵盤之前必須部署的滑動鍵盤。 在您啟用硬體鍵盤之前，模擬器只會接受來自控制鍵的按鍵輸入。  
  
 模擬器不支援 Windows 開發電腦當地語系化版本的鍵盤上有特殊字元。 若要輸入當地語系化鍵盤上存在的特殊字元，請改為使用軟體輸入面板 (SIP)。  
  
 若要在模擬器中使用您的電腦鍵盤，請按 PAGE UP 鍵或 PAUSE/BREAK 鍵 (Windows 8 8.1 模擬器) 或 F4 (Windows 10 模擬器)。  
  
 若要在模擬器中停止使用您的電腦鍵盤，請按 PAGE DOWN 鍵或 PAUSE/BREAK 鍵 (Windows 8 8.1 模擬器) 或 F4 (Windows 10 模擬器)。  
  
 下表列出硬體鍵盤上，可用於模擬 Windows Phone 上之按鈕及其他控制項的按鍵。  
  
|電腦硬體按鈕|Windows Phone 硬體按鈕|備註|  
|---------------------------|-----------------------------------|-----------|  
|F1|BACK|長按會如預期運作。|  
|F2|START|長按會如預期運作。|  
|F3|SEARCH||  
|F4|在 Windows 10 模擬器中，可在使用本機電腦的鍵盤與不使用本機電腦的鍵盤之間切換。|不適用於 Windows 8/8.1 模擬器。|  
|F5|不適用。||  
|F6|CAMERA HALF|按到一半的專用相機按鈕。|  
|F7|CAMERA FULL|專用相機按鈕。|  
|F8|不適用。||  
|F9|VOLUME UP||  
|F10|VOLUME DOWN||  
|F11|不適用。||  
|F12|POWER|按 F12 鍵兩次，即可啟用鎖定畫面。<br /><br /> 長按會如預期運作。|  
|ESC|BACK|長按會如預期運作。|  
|PAUSE/BREAK|切換鍵盤 (僅限 Windows 8/8.1 模擬器)。|不適用於 Windows 10 模擬器。|  
|PAGE UP|啟用硬體鍵盤 (僅限 Windows 8/8.1 模擬器)。|不適用於 Windows 10 模擬器。|  
|PAGE DOWN|停用硬體鍵盤 (僅限 Windows 8/8.1 模擬器)。|不適用於 Windows 10 模擬器。|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> 儲存及載入自訂檢查點  
 使用模擬器**其他工具**的 [**檢查點**] 索引標籤，儲存模擬器狀態的快照集。 如果您經常使用相同的資料和設定來測試應用程式，則此功能十分有用。  
  
 例如，如果您的應用程式需要數個連絡人，您可以一次建立連絡人記錄，並儲存模擬器的快照。 否則，每次啟動模擬器時，都需要重新建立連絡人記錄。  
  
- 按一下 [ **新增檢查點** ]，以在稍後再次測試您的應用程式時所需的資料和設定，以抓取模擬器狀態的新快照。 新的檢查點會新增至 **檢查點** 清單。  
  
   將偵錯工具附加至模擬器時，您無法擷取檢查點。  
  
- 在 [ **檢查點** ] 清單中選取檢查點，以查看檢查點的相關資訊。  
  
- 在 [ **預設** ] 資料行中選取選項按鈕，將儲存的檢查點設為使用中模擬器的預設檢查點。  
  
- 按一下 [ **還原** ]，重新開機模擬器上的 Windows Phone 作業系統，並載入選取的快照集。  
  
- 按一下 [ **刪除** ] 刪除您不再需要的快照。  
  
  原始模擬器映射一律會顯示為 **檢查點** 清單中的第一個專案，而且無法變更或刪除。 不過，您可以選取不同的快照做為預設模擬器影像。  
  
  ![Windows Phone 模擬器的 [檢查點] 索引標籤](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> 在模擬器中捕獲螢幕擷取畫面  
 您可以使用 [其他工具] 視窗中的螢幕擷取畫面工具，即可建立 Windows Phone 應用程式的螢幕擷取畫面。 此工具會建立符合執行中模擬器解析度的 PNG 檔案。  
  
 ![Windows Phone 模擬器的螢幕擷取畫面](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>使用內建模擬器螢幕擷取畫面工具建立應用程式螢幕擷取畫面  
  
1. 若要最佳化您螢幕擷取畫面的品質，請將模擬器的縮放層級設定為 100%。 您設定的縮放層級愈高，螢幕擷取畫面的品質就愈好。  
  
2. 在模擬器中啟動應用程式。  
  
3. 在模擬器工具列上，按一下展開按鈕以開啟 [ **其他工具** ] 視窗。  
  
4. 按一下 [ **螢幕擷取畫面** ] 索引標籤。  
  
5. 當您的應用程式就緒時，按一下 [ **捕捉** ] 按鈕。  
  
    螢幕擷取畫面即會顯示在工作區中。  
  
6. 按一下 [ **儲存** ] 按鈕以開啟 [ **另存** 新檔] 對話方塊。  
  
7. 選擇您想要的位置和 **檔案名** ，然後按一下 [ **儲存**]。  
  
8. 選擇性地，巡覽到您應用程式中的其他頁面，並擷取其他螢幕擷取畫面。  
  
9. 啟動螢幕解析度不同的模擬器，以擷取不同解析度的相同螢幕擷取畫面。 如果您已搭配執行應用程式與偵錯，則必須先停止偵錯，才能在另一個模擬器上重新執行應用程式。  
  
   先停用模擬器螢幕上的畫面播放速率計數器，再擷取將提交到 Windows Phone 市集的螢幕擷取畫面。  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>先停用模擬器中的畫面播放速率計數器，再擷取螢幕擷取畫面  
  
- 在 Visual Studio 中指定版本組建。 指定發行組建之後，請選取 [**組建**] 功能表上**的 _[部署 [應用程式名稱]]_ **連結來啟動您的應用程式。  
  
- 或者，您可以註解化 app.xaml.cs 或 app.xaml.vb 檔案中將 `EnableFrameRateCounter` 的值設為 `true` 的程式碼行。
