---
title: 在模擬器中執行 UWP 應用程式 |Microsoft Docs
description: 瞭解如何在 Visual Studio 模擬器（也就是模擬 UWP 應用程式的桌面應用程式）中執行通用 Windows 平臺 (UWP) 應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 12d2fed62e1a4762c9b92304ff1acfe8374ab976
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205628"
---
# <a name="run-uwp-apps-in-the-simulator"></a>在模擬器中執行 UWP 應用程式

適用于 UWP 應用程式的 Visual Studio 模擬器是可模擬 UWP 應用程式的桌面應用程式。 一般而言，您會想要在本機電腦、連線的裝置或遠端電腦上進行調試。 不過，在某些情況下，您可能會想要使用 Visual Studio 模擬器來模擬不同的實體螢幕大小和解析度。 您也可以模擬一般觸控和旋轉事件，以及模擬網路連接屬性。

模擬器會提供一個環境，讓您可以在其中設計、開發、偵測及測試 UWP 應用程式。 不過，在您將應用程式發佈至 Microsoft Store 之前，您應該先在實際裝置上測試您的應用程式。

UWP 應用程式的 Visual Studio 模擬器不會在本機電腦的隔離環境中執行。 因此，發生在模擬器中的錯誤，例如無法修復的全系統錯誤，也會影響到整部電腦。

> [!IMPORTANT]
> Visual Studio 2015 模擬器不包含 [地理位置] 按鈕。 這是因為 Windows 10 模擬器不包含地理位置模擬。

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> 將模擬器設定為目標

若要在模擬器中執行 UWP 應用程式，**請從調試** 程式 [**標準**] 工具列上 [**開始調試** 程式] 按鈕旁的下拉式清單中選取 [模擬器]。 只有當您應用程式的 **目標平台最低版本** 小於或等於您開發電腦上的作業系統時，才可以使用此選項。

![在模擬器中執行](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> 選擇互動模式

您可以選擇下列互動模式：

- ![滑鼠模式按鈕](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") 滑鼠模式：將互動模式設定為滑鼠手勢。 滑鼠動作包括按一下、按兩下和拖曳。

- ![啟動觸控模擬按鈕](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") 啟動觸控模擬：將互動模式設定為單一手指的觸控手勢。 單指事件包括點選，拖曳和撥動。

   ![模擬器單指目標](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   單一目標圖示表示模擬器中的事件位置。 使用滑鼠可以定位指標。

   ![單指觸碰目標](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   按下滑鼠左鍵可啟用觸控模式。 例如，按一下左鍵可以模擬點選，按住左鍵可以模擬拖曳或撥動。

## <a name="pinch-and-zoom"></a>縮小和放大

將互動模式設定為兩指的縮小和放大手勢。

![模擬器雙指目標](../debugger/media/simulator_twofinger.png)

雙目標圖示表示裝置螢幕上的兩指位置。

- 移動滑鼠可以將圖示定位至裝置螢幕上的物件。

- 向前或向後轉動滑鼠滾輪，可以變更您縮小或放大前的兩指模擬距離。

![縮小、放大和旋轉目標](../debugger/media/simulator_twofingerengaged.png)

- 按住左鍵並向後旋轉滾輪 (朝向您的方向) 可以拉近 (縮小)。

- 按住左鍵並向前旋轉滾輪 (遠離您的方向) 可以拉遠 (放大)。

## <a name="object-rotation"></a>物件旋轉

[觸控模擬旋轉]  按鈕將互動模式設定為運用兩指的旋轉手勢。

- 移動滑鼠可以將圖示定位至裝置螢幕上的物件。 向前或向後轉動滑鼠滾輪，可以變更您旋轉物件前的兩指模擬方向。

- 按住左鍵並向後旋轉滾輪 (朝向您的方向) 可以逆時針旋轉物件。 在旋轉滑鼠滾輪時，這兩個目標圖示的其中一個會沿著另一個圖示旋轉，指出旋轉的相對大小。

- 按住左鍵並向前旋轉滑鼠滾輪 (遠離您的方向) 可以順時針旋轉物件。

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> 啟用或停用最上層顯示模式
 您可以將模擬器視窗設定為永遠在其他視窗的最上層。 [切換最上層的視窗]  按鈕可啟用或停用模擬器視窗的 [最上層顯示]  模式。

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> 變更裝置方向
 將模擬器往任意方向旋轉 90 度，即可在縱向或橫向之間切換裝置方向。

> [!NOTE]
> 模擬器不接受專案的 [DisplayProperties.AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) 屬性。 例如，如果您的專案將方向設定為 `Landscape`，接著您將模擬器旋轉為縱向方向，則模擬器顯示影像也會據以旋轉並調整大小。 在實際裝置上測試這些設定。

> [!NOTE]
> 如果因為旋轉模擬器而使得模擬器的某一邊大於所顯示螢幕的同一邊，模擬器會自動調整大小以便符合螢幕。 如果再次旋轉模擬器，模擬器不會重新調整回其原始大小。

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> 變更模擬的螢幕大小和解析度
 若要變更模擬的螢幕大小與解析度，請從調色盤上選擇 [變更解析度]  按鈕，並從清單中選擇新的大小與解析度。

 螢幕大小和解析度列示為 *螢幕寬度英吋，像素 X 像素高度*。 請注意，螢幕大小和解析度都是模擬的。 模擬器上的位置座標會轉譯成所選裝置大小和解析度。

> [!NOTE]
> 您可以將點陣圖影像的已調整版本儲存在您的應用程式中，Windows 會載入目前比例的正確影像。 如需詳細資訊，請參閱 [設計和 UI 簡介](/windows/uwp/layout/design-and-ui-intro)。 不過，如果您變更了模擬器解析度，因此 Windows 選擇了不同的影像來符合解析度，則您必須停止並重新開始偵錯工作階段，才能檢視新影像。

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> 捕捉您的應用程式的螢幕擷取畫面，以提交給 Microsoft Store
 當您將應用程式提交至 Microsoft Store 時，您必須包含應用程式的螢幕擷取畫面。

> [!NOTE]
> 螢幕擷取畫面會以模擬器的目前解析度儲存。 若要變更解析度，請選擇 [ **變更解析度** ] 按鈕。

- 若要從模擬器建立您的應用程式的螢幕擷取畫面，請選擇 [ **擷取螢幕擷取畫面到剪貼簿** ] 按鈕。

- 若要設定螢幕擷取畫面的所在位置，請選擇 [螢幕擷取畫面設定]  按鈕，並從捷徑功能表中選擇位置。

   ![螢幕擷取畫面設定操作功能表](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> 模擬網路連接屬性

您可以藉由維護網路連線成本或數據傳輸方案狀態變更的感知，並讓您的應用程式使用此資訊來避免因為漫遊或超出指定的資料傳輸限制而產生額外費用，協助應用程式使用者管理計量付費網路連接的費用。 [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) API 可讓您回應簽署的 [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) 和 [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) 事件。 請參閱 [快速入門：管理計量付費網路費用限制](/previous-versions/windows/apps/hh750310(v=win.10))。

若要偵錯或測試您的網路成本感知程式碼，模擬器可以模擬透過 [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation) 傳回的 [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) 物件所公開之網路屬性。

若要模擬網路屬性：

1. 在模擬器工具列上，選擇 [變更網路屬性]  按鈕。

2. 在 [設定網路屬性]  對話方塊中，選取 [使用模擬的網路屬性] 。

    清除核取方塊移除模擬，並返回目前連接介面的網路屬性。

3. 為模擬的網路輸入 [ **設定檔名稱** ]。 建議您使用不重複的名稱，以便在 [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) 物件的 [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) 屬性中，能識別此模擬。

4. 從 [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) 清單中，為設定檔選取 **NetworkCostType** 值。

5. 從 [資料限制狀態旗標] 清單中，可以將 [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) 屬性或 [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) 屬性設定為 true，也可以選擇 [低於資料限制]，將兩個值皆設定為 false。

6. 從 [漫遊狀態]  清單，設定 [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) 屬性。

7. 選擇 [設定屬性]  ，透過觸發前景 [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) 事件和 [NetworkStateChange](/uwp/api/windows.applicationmodel.background.systemtrigger) 類型的背景 **SystemTrigger** 來模擬網路屬性。

如需管理網路連接的詳細資訊，請參閱：

[快速入門：管理計量付費網路費用限制](/previous-versions/windows/apps/hh750310(v=win.10))

[網路資訊範例](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[分析能源利用](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[如何使用背景工作回應系統事件](/previous-versions/windows/apps/hh977058(v=win.10))

[如何在 UWP App 中觸發暫停、繼續和背景事件](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> 使用鍵盤巡覽模擬器

您可以按 **CTRL + ALT + 向上鍵** 流覽模擬器工具列，將焦點從模擬器視窗切換至模擬器工具列。 使用 **向上鍵** 和 **向下鍵** 可以在工具列按鈕之間移動。

您可以按 **CTRL + ALT + F4** 來關閉模擬器。

## <a name="see-also"></a>請參閱

- [從 Visual Studio 執行應用程式](debugging-windows-store-and-windows-universal-apps.md)