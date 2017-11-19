---
title: "UWP 和 Windows 8.1 應用程式在模擬器中執行 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf4c5d1e71a4d0e0d8ac74ba02bff29ddc1c7477
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-and-windows-81-apps-in-the-simulator"></a>在模擬器中執行的 UWP 和 Windows 8.1 應用程式
UWP 和 Windows 8.1 應用程式的 Visual Studio 模擬器是桌面應用程式，可以模擬 UWP 或 Windows 8.1 的應用程式。 您可以執行的應用程式選擇的實體螢幕大小和您要模擬的解析度。 您也可以模擬常見觸控和旋轉事件，以及模擬網路連接屬性。
  
 模擬器會提供的環境，在其中您可以設計、 開發、 偵錯和測試 UWP 應用程式。 不過，您發行至 Microsoft Store 的應用程式之前，您應該測試您的應用程式，在實際裝置上。  
  
 UWP 應用程式的 Visual Studio 模擬器不會在本機電腦上執行的隔離環境中。 因此，發生在模擬器中的錯誤，例如無法修復的全系統錯誤，也會影響到整部電腦。  
  
 如需 Windows Phone 資訊，請參閱 [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) 。  
  
> [!IMPORTANT]
>  Visual Studio 2015 模擬器不包含 [地理位置] 按鈕。 這是因為 Windows 10 模擬器不包含地理位置模擬。 如果您需要執行這類模擬，您可以在 Windows 8.1 或舊版作業系統上使用 Visual Studio 2013 模擬器。  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> 將模擬器設定為目標  
 若要在 UWP 應用程式在模擬器中執行，請選取**模擬器**旁的下拉式清單**開始偵錯**偵錯工具的按鈕**標準**工具列。  
  
 ![在模擬器中執行](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> 選擇互動模式  
 您可以選擇下列互動模式  
  
-   ![滑鼠模式按鈕](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn")滑鼠模式： 將互動模式設定為滑鼠動作。 滑鼠動作包括按一下、按兩下和拖曳。  
  
-   ![啟動觸控模擬 按鈕](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn")啟動觸控模擬： 將互動模式設定指觸控手勢單一。 單指事件包括點選，拖曳和撥動。  
  
     ![模擬器單指目標](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")單一目標圖示表示模擬器中的事件位置。 使用滑鼠可以定位指標。  
  
     ![單指觸碰目標](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")按下滑鼠左的按鈕可啟用觸控模式。 例如，按一下左鍵可以模擬點選，按住左鍵可以模擬拖曳或撥動。  
  
## <a name="pinch-and-zoom"></a>縮小和放大  
 將互動模式設定為兩指的縮小和放大手勢。  
  
-   ![模擬器兩指目標](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     雙目標圖示表示裝置螢幕上的兩指位置。  
  
    -   移動滑鼠可以將圖示定位至裝置螢幕上的物件。  
  
    -   向前或向後轉動滑鼠滾輪，可以變更您縮小或放大前的兩指模擬距離。  
  
-   -   ![縮小、 放大和旋轉目標](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         按住左鍵並向後旋轉滾輪 (朝向您的方向) 可以拉近 (縮小)。  
  
    -   按住左鍵並向前旋轉滾輪 (遠離您的方向) 可以拉遠 (放大)。  
  
## <a name="object-rotation"></a>物件旋轉  
 [觸控模擬旋轉]  按鈕將互動模式設定為運用兩指的旋轉手勢。  
  
-   -   移動滑鼠可以將圖示定位至裝置螢幕上的物件。  
  
    -   向前或向後轉動滑鼠滾輪，可以變更您旋轉物件前的兩指模擬方向。  
  
-   -   按住左鍵並向後旋轉滾輪 (朝向您的方向) 可以逆時針旋轉物件。 在旋轉滑鼠滾輪時，這兩個目標圖示的其中一個會沿著另一個圖示旋轉，指出旋轉的相對大小。  
  
    -   按住左鍵並向前旋轉滑鼠滾輪 (遠離您的方向) 可以順時針旋轉物件。  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> 啟用或停用最上層顯示模式  
 您可以將模擬器視窗設定為永遠在其他視窗的最上層。 [切換最上層的視窗]  按鈕可啟用或停用模擬器視窗的 [最上層顯示]  模式。  
  
##  <a name="BKMK_Change_the_device_orientation"></a> 變更裝置方向  
 將模擬器往任意方向旋轉 90 度，即可在縱向或橫向之間切換裝置方向。  
  
> [!NOTE]
>  模擬器不接受專案的 [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) 屬性。 例如，如果您的專案將方向設定為 `Landscape`，接著您將模擬器旋轉為縱向方向，則模擬器顯示影像也會據以旋轉並調整大小。 在實際裝置上測試這些設定。  
  
> [!NOTE]
>  如果因為旋轉模擬器而使得模擬器的某一邊大於所顯示螢幕的同一邊，模擬器會自動調整大小以便符合螢幕。 如果再次旋轉模擬器，模擬器不會重新調整回其原始大小。  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> 變更模擬的螢幕大小和解析度  
 若要變更模擬的螢幕大小與解析度，請從調色盤上選擇 [變更解析度]  按鈕，並從清單中選擇新的大小與解析度。  
  
 螢幕大小和解析度列示為 *螢幕寬度英吋，像素 X 像素高度*。 請注意，螢幕大小和解析度都是模擬的。 模擬器上的位置座標會轉換為已選取裝置大小和解析度的座標。  
  
> [!NOTE]
>  您可以將點陣圖影像的已調整版本儲存在您的應用程式中，Windows 會載入目前比例的正確影像。 如需詳細資訊，請參閱[設計和 UI 的入門](/windows/uwp/layout/design-and-ui-intro)。 不過，如果您變更了模擬器解析度，因此 Windows 選擇了不同的影像來符合解析度，則您必須停止並重新開始偵錯工作階段，才能檢視新影像。  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>擷取螢幕擷取畫面以提交至 Microsoft 市集應用程式  
 當您提交至 Microsoft 市集應用程式時，您必須包含應用程式的螢幕擷取畫面。  
  
> [!NOTE]
>  螢幕擷取畫面會以模擬器的目前解析度儲存。 若要變更解析度，請選擇 [ **變更解析度** ] 按鈕。  
  
-   若要從模擬器建立您的應用程式的螢幕擷取畫面，請選擇 [ **擷取螢幕擷取畫面到剪貼簿** ] 按鈕。  
  
-   若要設定螢幕擷取畫面的所在位置，請選擇 [螢幕擷取畫面設定]  按鈕，並從捷徑功能表中選擇位置。  
  
     ![螢幕擷取畫面設定操作功能表](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> 模擬網路連接屬性  
 您可以協助您的應用程式使用者管理計量付費的網路連接的費用，藉由維護網路連接成本或資料方案狀態變更的感知，以及啟用您的應用程式使用此資訊來避免因為漫遊或超出額外費用指定的資料傳輸限制。 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) Api 可讓您回應[NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation)和[TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger)登入的事件。 請參閱 [快速入門：管理計量付費網路費用限制](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)。  
  
 若要偵錯或測試您的網路成本感知程式碼，模擬器可以模擬透過公開的網路屬性[ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile)所傳回物件[Connectionprofile](/uwp/api/windows.networking.connectivity.networkinformation)。
  
 若要模擬網路屬性：  
  
1.  在模擬器工具列上，選擇 [變更網路屬性]  按鈕。  
  
2.  在 [設定網路屬性]  對話方塊中，選取 [使用模擬的網路屬性] 。  
  
     清除核取方塊移除模擬，並返回目前連接介面的網路屬性。  
  
3.  為模擬的網路輸入 [ **設定檔名稱** ]。 我們建議使用唯一的名稱可讓您識別此模擬中的[ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile)屬性[ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile)物件。  
  
4.  選取[NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype)值的設定檔**網路成本類型**清單。  
  
5.  從**資料限制狀態旗標**清單中，您可以將[ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)屬性或[OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost)屬性設定為 true，或者您可以選擇**在 資料限制下**這兩個值設定為 false。  
  
6.  從**漫遊狀態**清單中，設定[漫遊](/uwp/api/windows.networking.connectivity.connectioncost)屬性。  
  
7.  選擇**設定屬性**來模擬網路屬性，透過觸發前景[NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation)事件和背景[SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) 型別**NetworkStateChange**。  
  
 **管理網路連接的詳細資訊**  
  
 [快速入門：管理計量付費網路費用限制](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [網路資訊範例](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [分析能源利用](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
 [如何使用背景工作回應系統事件](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [如何觸發暫止、 繼續及背景事件在 UWP 應用程式](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> 使用鍵盤巡覽模擬器  
 您可以藉由按下巡覽模擬器工具列**CTRL + ALT + 向上鍵**將焦點從模擬器視窗切換至模擬器工具列。 使用 **向上鍵** 和 **向下鍵** 可以在工具列按鈕之間移動。  
  
 您可以藉由按下關閉模擬器**CTRL + ALT + F4**。  
  
## <a name="see-also"></a>另請參閱  
 [從 Visual Studio 執行應用程式](../debugger/run-store-apps-from-visual-studio.md)