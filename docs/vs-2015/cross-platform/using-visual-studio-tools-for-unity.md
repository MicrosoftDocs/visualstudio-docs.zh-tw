---
title: 使用 Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1b99999c3a075b6e79f2b98fc70cf50a9d01a84d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892827"
---
# <a name="using-visual-studio-tools-for-unity"></a>使用 Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
在本節中，您將了解如何使用 Visual Studio Tools for Unity 的整合和產能功能，以及如何針對 Unity 開發使用 Visual Studio 偵錯工具。  
  
## <a name="unity-integration-and-productivity"></a>Unity 整合和產能  
 Visual Studio Tools for Unity 與 Unity Editor 的整合有助於提升您的產能。 這些提升產能的功能包括將常見的指令碼工作自動化，以及將 Unity 中的資訊帶入 Visual Studio，讓您不需要切換至 Unity Editor 尋找資訊。  
  
### <a name="unity-documentation-access"></a>Unity 文件存取  
 您可以從 Visual Studio 快速存取 Unity 指令碼文件。 如果 Visual Studio Tools for Unity 在本機找不到應用程式開發介面文件，則會嘗試在線上尋找。  
  
##### <a name="to-access-unity-documentation"></a>存取 Unity 文件  
  
-   在 Visual Studio 中，反白顯示您要了解的 Unity API 或將游標置於其上，然後按 **Ctrl+Alt+M、Ctrl+H**  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior 指令碼精靈  
 在 Unity 中，大部分指令碼的實作方式，不是透過衍生自 MonoBehavior 類別，就是透過覆寫其中一些方法。 您可以使用 MonoBehavior 精靈，為要多載的 MonoBehavior 方法快速建立空白定義。 透過這個精靈，您可以從可用方法清單中指定一個或多個要多載的方法、選擇要在程式碼中插入這些方法的位置，以及決定是否要包含這些方法的使用方式註解。  
  
 ![MonoBehavior 精靈對話方塊。](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>使用 MonoBehavior 精靈建立空白 MonoBehavior 方法定義  
  
1. 在 Visual Studio 中，將游標置於您要插入方法的位置，然後按 **Ctrl+Shift+M** 啟動 MonoBehavior 精靈。 或者，如果您想要在已實作的某個方法之後插入新方法，您可以稍後再指定；此時只要按 **Ctrl+Shift+M**。  
  
2. 選取您要多載的方法。 在 [建立指令碼方法] 視窗的 [選取要建立的方法] 底下，標記您要多載之每個方法名稱旁的核取方塊。  
  
3. 確定 [Framework 版本] 下拉式清單中的 Framework 版本符合您所使用的版本。 如果不符，請將下拉式清單中的值變更為您要使用的版本。  
  
4. 選擇要插入方法的位置。 預設會在游標位置插入方法；如果您想要將方法插入其他位置，您可以選擇將其插入類別中已實作的任何方法之後。 若要選擇其中一個位置，請將 [插入點] 下拉式清單中的值變更為您要的位置。  
  
5. 如果您希望精靈為您選取的方法產生註解，請標記 [產生方法註解] 核取方塊。 這些註解可協助您了解何時呼叫方法，以及方法的一般責任為何。  
  
6. 選擇 [確定] 按鈕以結束精靈，並將方法插入到您的程式碼。  
  
   如果您還在學習 Unity 應用程式開發介面，或者需要多載您不熟悉的方法，MonoBehavior 精靈特別有用。 當您較熟悉如何使用 Unity 應用程式開發介面時，您可能會偏好讓 Quick MonoBehavior 精靈快速建立您已熟悉的方法。  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Quick MonoBehavior 指令碼精靈  
 當您熟悉 Unity 應用程式開發介面之後，您可以使用 Quick MonoBehavior 精靈更快地實作多載方法。 透過這個精靈，您可以指定已插入游標位置之不含方法註解的單獨一個方法。  
  
 ![Quick MonoBehavior 精靈對話方塊。](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>使用 Quick MonoBehavior 精靈建立空白 MonoBehavior 方法定義  
  
1.  在 Visual Studio 中，將游標置於您要插入方法的位置，然後按 **Ctrl+Shift+Q** 啟動 Quick MonoBehavior 精靈。 不同於另一個 MonoBehavior 精靈，由於新方法一律已插入該位置，因此您必須在使用這個精靈時，刻意置放游標。  
  
2.  確定顯示在 [建立指令碼方法] 視窗右上角的 Framework 版本符合您所使用的版本。 如果不符，請將下拉式清單中的值變更為您要使用的版本。  
  
3.  尋找您要多載的方法。 在 [Create script method] 視窗的文字方塊中，開始輸入方法的名稱。 其名稱符合您輸入內容的方法清單會隨即出現。  
  
4.  選擇您要多載的方法。 如果您要的方法顯示在清單中，請以滑鼠或方向鍵選取它，然後按 **Enter**。 如果該方法是清單中的唯一方法，您可以直接按 **Enter**。 該方法會隨即插入您的程式碼。  
  
### <a name="unity-project-explorer"></a>Unity Project Explorer  
 您可以在 Visual Studio 中，使用 Unity Project Explorer 來巡覽 Unity 專案。  
  
 ![Unity 專案總管視窗。](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>檢視 Unity Project Explorer  
  
- 在 Visual Studio 主功能表上，選擇 [檢視]、[Unity 專案總管]。 鍵盤：**Alt+Shift+E**  
  
   ![檢視 Unity 專案總管視窗。](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Unity Project Explorer 使用與 Unity Editor 相同的方式，來顯示所有 Unity 專案檔和目錄。這不同於使用方案總管來巡覽 Unity 指令碼，方案總管只會包含您的指令碼檔案，並將這些檔案顯示為 Visual Studio Tools for Unity 所產生、用於組織檔案的專案和方案。 特別是在大型專案中，使用 Unity Project Explorer 通常更容易找到您要修改的指令碼；在 Visual Studio 中修改其他類型的檔案 (例如文字型組態檔) 也很輕鬆，您不需要將這些檔案加入 Visual Studio 方案的其中一個專案。  
  
### <a name="unity-error-list"></a>Unity 錯誤清單  
 您可以在 Visual Studio 連接到 Unity 執行個體時，於 Visual Studio 中檢視來自 Unity 主控台的訊息。 其中包括來自 Unity 的錯誤和警告。 這些訊息會顯示在 Visual Studio 的 [錯誤清單] 視窗中；來自 Unity 的錯誤訊息會顯示在 [錯誤] 索引標籤上，警告訊息會顯示在 [警告] 索引標籤上，而其他訊息 (例如使用 Debug.Log Unity API 傳送的訊息) 則會顯示在 [訊息] 索引標籤上。  
  
 若要查看訊息，您的 Unity 專案必須[在 Unity 播放器中為您的專案偵錯](#debugging-your-project-in-a-unity-player)，以支援「指令碼偵錯」並匯入適用於您的 Visual Studio 版本的 Visual Studio Tools for Unity 套件，且 Visual Studio 必須[將 Visual Studio 連接到 Unity](#connecting-visual-studio-to-unity)。  
  
 如果您不想要在 Visual Studio 的 [錯誤清單] 視窗中看到來自 Unity 的錯誤、警告和訊息，您可以在 [組態] 功能表中予以停用。  
  
### <a name="keyboard-shortcuts"></a>鍵盤快速鍵  
 您可以使用鍵盤快速鍵快速存取 Unity Tools for Visual Studio 功能。 以下是可用的快速鍵摘要。  
  
|命令|快速鍵|快速鍵命令名稱|  
|-------------|--------------|---------------------------|  
|開啟 MonoBehavior 精靈|**Ctrl+Shift+M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|  
|開啟 Quick MonoBehavior 精靈|**Ctrl+Shift+Q**|**EditorContextMenus.CodeWindow.QuickMonoBehaviours**|  
|開啟 Unity Project Explorer|**Alt+Shift+E**|**View.UnityProjectExplorer**|  
|存取 Unity 文件|**Ctrl+Alt+M、Ctrl+H**|**Help.UnityAPIReference**|  
|附加至 Unity 偵錯工具 (播放器或編輯器)|**無預設值**|**Debug.AttachUnityDebugger**|  
  
 如果您不喜歡預設值，可以變更快速鍵組合。 如需如何變更它的詳細資訊，請參閱[識別及自訂 Visual Studio 中的鍵盤快速鍵](https://msdn.microsoft.com/library/5zwses53.aspx)。  
  
## <a name="unity-debugging"></a>Unity 偵錯  
 Visual Studio Tools for Unity 可讓您使用 Visual Studio 的強大偵錯工具，同時對 Unity 專案的編輯器和遊戲指令碼進行偵錯。  
  
###  <a name="connecting-visual-studio-to-unity"></a> 將 Visual Studio 連接到 Unity  
 Visual Studio Tools for Unity 透過 UDP 連接與 Unity 通訊。 這表示連接到在本機或網路上任何位置執行的 Unity 執行個體的方式完全相同。 您可以使用 [選取 Unity 執行個體] 對話方塊，連接到網路上可見的任何 Unity 執行個體。  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>開啟 [Select Unity Instance] 對話方塊  
  
-   在 Visual Studio 主功能表上，選擇 [偵錯]、[附加 Unity 偵錯工具]。  
  
     ![附加 Unity 的偵錯工具。](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
-   或者，在 Visual Studio 中，選擇 Visual Studio 右下角狀態列上的插頭圖示。  
  
     ![這個圖示顯示 VSTU 已連接到 Unity。](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
>  如果插頭圖示顯示一個勾選記號，則表示您已連接到 Unity 執行個體。  
  
 [選取 Unity 執行個體] 對話方塊會顯示您可連接之每個 Unity 執行個體的一些資訊。  
  
 ![選擇要連接到的 Unity 執行個體。](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Project**  
 在這個 Unity 執行個體中執行的 Unity 專案名稱。  
  
 **Machine**  
 這個 Unity 執行個體執行所在的電腦或裝置名稱。  
  
 **Type**  
 如果這個 Unity 執行個體當做 Unity Editor 的一部分來執行，則為 **Editor**；如果這個 Unity 執行個體是獨立播放器，則為 **Player**。  
  
 **連接埠**  
 這個 Unity 執行個體用於通訊之 UDP 通訊端的通訊埠編號。  
  
> [!IMPORTANT]
>  由於 Visual Studio Tools for Unity 是透過 UDP 網路通訊端與 Unity 執行個體通訊，因此您的防火牆可能會要求這項資訊。 如果發生這種情況，您必須授權連接，VSTU 和 Unity 才能通訊。  
  
###  <a name="debugging-your-project-in-a-unity-player"></a> 在 Unity 播放器中為專案偵錯  
 如果沒有執行 Unity Editor，您可以將 Visual Studio Tools for Unity 直接連接到在獨立播放器中執行的 Unity 應用程式，您也可以透過這個方式來偵錯平台特定的問題。  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>在 Unity 播放器中啟用指令碼偵錯  
  
- 確定您在建立開發組建時，已啟用指令碼偵錯。 在 Unity 專案的組建設定中，標記 [開發建置] 和 [指令碼偵錯] 核取方塊。  
  
  ![設定用於偵錯的 Unity 組建設定。](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  此外，若要為在 **Unity Web Player** 中執行的 Unity 應用程式偵錯，還需要設定播放器以使用 [Development Release Channel]。  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>在 Unity Web Player 中設定 Development Release Channel  
  
- 在 Unity Web Player 的操作功能表上，選擇 [Release Channel]，並確定已啟用 [Development] 選項。  
  
  > [!IMPORTANT]
  >  在 Unity 4.2 (含) 以後版本中，只有 Web Player 操作功能表才會提供 [Release Channel] 操作功能表項目 (在開啟操作功能表時按 **Alt** 鍵)。 如果 Web Player 是在 Mac OS X 上執行，請改按 **Option** 鍵。  
  
  最後，請確定您已連接到要偵錯的 Unity 執行個體。 如需如何執行此動作的相關資訊，請參閱[將 Visual Studio 連接到 Unity](#connecting-visual-studio-to-unity) 一節。  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>為 Unity 專案中的 DLL 偵錯  
 許多 Unity 開發人員會將程式碼元件撰寫成外部 DLL，以便與其他專案共用他們所開發的功能。 Visual Studio Tools for Unity 可讓您順暢地連同 Unity 專案中的其他程式碼一起為這些 DLL 中的程式碼偵錯。  
  
> [!NOTE]
>  目前，Visual Studio Tools for Unity 僅支援 Managed DLL， 並不支援對機器碼 DLL 進行偵錯 (例如以 C++ 撰寫的 DLL)。  
  
 請注意，此處所述的情節假設您有原始程式碼；也就是說，您正在開發或重複使用自己的第一方程式碼，或您有協力廠商程式庫的程式碼，並打算將其部署至 Unity 專案中做為 DLL。 該情節不會說明如何對您沒有原始程式碼的 DLL 進行偵錯。  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>為 Unity 專案所使用的 Managed DLL 專案偵錯  
  
1. 將現有的 DLL 專案加入 Visual Studio Tools for Unity 所產生的 Visual Studio 方案。 在較不常見的情況下，您可能會啟動新的 Managed DLL 專案來包含 Unity 專案中的程式碼元件；如果是這種情況，您可以改為將新的 Managed DLL 專案加入 Visual Studio 方案。 如需將新的或現有的專案加入至方案的詳細資訊，請參閱[作法：將專案加入至方案](https://msdn.microsoft.com/library/vstudio/ff460187.aspx)。  
  
    ![將現有的 DLL 專案加入至方案。](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    不論是哪一種情況，Visual Studio Tools for Unity 都會保留專案參考 (即使必須再次重新產生專案和方案檔亦然)，因此您只需要執行這些步驟一次。  
  
2. 參考 DLL 專案中的正確 Unity Framework 設定檔。 在 Visual Studio 的 DLL 專案屬性中，將 [目標 Framework] 屬性設定為您所使用的 Unity Framework 版本。 這是與專案的目標應用程式開發介面相容的 Unity 基底類別庫，例如 Unity 完整、微型或 Web 基底類別庫。 如此可防止 DLL 呼叫存在於其他 Framework 或相容性層級中，但可能不存在於您所使用之 Unity Framework 版本的 Framework 方法。  
  
    ![將 DLL 的目標 Framework 設定為 Unity 架構。](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. 將 DLL 複製到 Unity 專案的 Assets 資料夾。 在 Unity 中，資產是與 Unity 應用程式一起封裝及部署的檔案，以便可以在執行階段載入。 由於 DLL 是在執行階段連結，因此您必須將 DLL 部署為資產。 為了將 DLL 部署為資產，Unity Editor 會要求將 DLL 放在 Unity 專案的 [Assets] 資料夾中。 有兩種方式可讓您完成這個步驟：  
  
   - 修改 DLL 專案的組建設定，以包含將輸出 DLL 和 PDB 檔案從其輸出資料夾複製到 Unity 專案之 [Assets] 資料夾的建置後工作。  
  
   - 修改 DLL 專案的組建設定，將其輸出資料夾設定為 Unity 專案的 [Assets] 資料夾。 DLL 和 PDB 檔案都會被放在 [Assets] 資料夾中。  
  
     由於 PDB 檔案包含 DLL 的偵錯符號，並將 DLL 程式碼對應至其原始程式碼形式，因此偵錯時會需要這些檔案。 Visual Studio Tools for Unity 將會使用 DLL 和 PDB 中的資訊來建立 DLL.MDB 檔案，這是 Unity 指令碼引擎所使用的偵錯符號格式。  
  
4. 為程式碼偵錯。 您現在可以連同 Unity 專案的原始程式碼一起為 DLL 原始程式碼偵錯，並使用您慣用的所有偵錯功能，例如中斷點和逐步執行程式碼。

