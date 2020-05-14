---
title: 使用 Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d1bca9bed18de822de71ca441387adeaefc65ec3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649389"
---
# <a name="use-visual-studio-tools-for-unity"></a>使用 Visual Studio Tools for Unity

在本節中，您將了解如何使用 Visual Studio Tools for Unity 的整合和產能功能，以及如何針對 Unity 開發使用 Visual Studio 偵錯工具。

## <a name="open-unity-scripts-in-visual-studio"></a>在 Visual Studio 中開啟 Unity 指令碼

將 Visual Studio [設定為 Unity 的外部指令碼編輯器](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)，在開啟所選擇指令碼的情況下，從 Unity 編輯器中開啟任何指令碼將會自動啟動或切換至 Visual Studio。 只要按兩下您 Unity 專案中的指令碼即可。

或者，從 Unity 的 [資產]**** 功能表選取 [Open C# Project] \(開啟 C# 專案\)****，也可以在原始檔編輯器中未開啟任何指令碼的情況下開啟 Visual Studio。

![開啟 C# 專案](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Unity 文件存取

您可以從 Visual Studio 快速存取 Unity 指令碼文件。 如果 Visual Studio Tools for Unity 在本機找不到應用程式開發介面文件，則會嘗試在線上尋找。

- 在可檢視化工作室中,突出顯示游標或將游標放在要瞭解的 Unity API 上,然後按**Ctrl**+**Alt**+**M** **,Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>Unity API 訊息的 IntelliSense

Intellisense 程式碼編譯可在 MonoBehaviour 指令碼中輕鬆地實作 Unity API 訊息，並協助了解 Unity API。 使用適用於 Unity 訊息的 IntelliSense：

1. 將游標放在衍生自 `MonoBehaviour` 之類別主體內的新行。

2. 開始鍵入 Unity 訊息的名稱，例如 `OnTriggerEnter`。

3. 一旦鍵入 「**ontri**" 字母之後，會出現 IntelliSense 建議清單。

   ![Using IntelliSense](media/vstu_intellisense1.png)

4. 有三種方式可以變更清單上的選項：

    - 使用向上**** 和向下**** 方向鍵。

    - 使用滑鼠按一下所需的項目。

    - 繼續鍵入所需項目的名稱。

5. IntelliSense 可以插入選取的 Unity 訊息，包含任何必要參數：

    - 按 **Tab**。

    - 按 **Enter**。

    - 按兩下選取的項目。

   ![從 IntelliSense 插入 Unity 訊息](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior 指令碼精靈

您可以使用 MonoBehavior 精靈來檢視所有 Unity API 方法清單，並快速實作空白的定義。 若您仍在了解 Unity API 中可用的項目有哪些，此功能 (特別是在已啟用 [產生方法註解]**** 選項時) 非常實用。

使用 MonoBehavior 精靈建立空白 MonoBehavior 方法定義：

1. 在 Visual Studio 中,將游標放置在要插入方法的位置,然後按**Ctrl**+**Shift**+**M**啟動單行為精靈。

2. 在 [建立指令碼方法]**** 視窗中，標記您要加入之每個方法名稱旁的核取方塊。

3. 使用 [Framework 版本]**** 下拉式清單來選取您想要的版本。

4. 根據預設，方法會插入到游標所在位置。 或者，您可以選擇將它們插入到已在您的類別中實作的任何方法之後，方法是將 [插入點]**** 下拉式清單的值變更為您想要的位置。

5. 如果您希望精靈為您選取的方法產生註解，請標記 [產生方法註解]**** 核取方塊。 這些註解可協助您了解何時呼叫方法，以及方法的一般責任為何。

6. 選擇 [確定]**** 按鈕以結束精靈，並將方法插入到您的程式碼。

   ![單一行為精靈對話方塊。](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Unity Project Explorer

![Unity 專案總管視窗。](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity 專案總管會使用與 Unity 編輯器一樣的方式顯示您的所有 Unity 專案檔案與目錄。 這與使用一般 Visual Studio 方案總管瀏覽 Unity 指令碼的方式不同，一般 Visual Studio 方案總管會將它們組織為專案與 Visual Studio 產生的方案。

- 在 Visual Studio 主功能表上，選擇 [檢視] > [Unity 專案總管]****。 鍵盤捷徑 **:Alt**+**移位**+**E**

   ![檢視 Unity 專案總管視窗。](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Unity 偵錯

Visual Studio Tools for Unity 可讓您使用 Visual Studio 的強大偵錯工具，同時對 Unity 專案的編輯器和遊戲指令碼進行偵錯。

### <a name="debug-in-the-unity-editor"></a>在 Unity 編輯器中偵錯

#### <a name="start-debugging"></a>開始偵錯

1. 按一下標籤為 [附加至 Unity]**** 的 [播放]**** 按鈕，或使用鍵盤快速鍵 **F5** ，以將 Visual Studio 附加至 Unity。

   ![在 Visual Studio 中按一下 [播放]](media/vstu_play-button.png)

2. 切換至 Unity，然後按一下 [播放]**** 按鈕，以在編輯器中執行遊戲。

   ![在 Unity 中按一下 [播放]](media/vstu_unity-play-button.png)

3. 如果遊戲在連線至 Visual Studio 時於 Unity 編輯器中執行，則遇到的任何中斷點都會暫停執行遊戲，並啟動遊戲在 Visual Studio 中叫用中斷點的一行程式碼。

#### <a name="stop-debugging"></a>停止偵錯

- 在 Visual Studio 中按一下 [停止]**** 按鈕，或使用鍵盤快速鍵 **Shift + F5**。

  ![在 Visual Studio 中按一下 [停止]](media/vstu_stop-debugger.png)

若要深入了解如何在 Visual Studio 中進行偵錯，請參閱[搶先了解 Visual Studio 偵錯工具](../debugger/debugger-feature-tour.md)。

#### <a name="attach-to-unity-and-play"></a>附加至 Unity 並試玩

如果要方便執行，您可以將 [附加至 Unity]**** 按鈕變更為 [附加至 Unity 並試玩]**** 模式。

1. 按一下 [附加至 Unity]**** 按鈕旁的小型**下拉式箭頭**。

1. 從下拉式功能表選取 [附加至 Unity 並試玩]****。

    ![附加並試玩](media/vstu_attach-and-play.png)

[播放] 按鈕的標籤會變成 [附加至 Unity 並試玩]****。 除了附加 Visual Studio 偵錯工具之外，按一下此按鈕或使用鍵盤快速鍵 **F5** 現在會自動切換到 Unity 編輯器並在編輯器中執行遊戲。

在 Visual Studio 中按一下 [停止]**** 按鈕或使用鍵盤快速鍵 **Shift**+**F5** 將會自動停止 Unity 編輯器中的遊戲。

### <a name="debug-unity-player-builds"></a>針對 Unity 玩家組建進行偵錯

您可以使用 Visual Studio 為不同 Unity 玩家的開發組建進行偵錯。

#### <a name="enable-script-debugging-in-a-unity-player"></a>在 Unity 播放器中啟用指令碼偵錯

1. 在 Unity 中，選取 [檔案] > [組建設定]**** 以開啟 [組建設定]。

2. 在 [組建設定] 視窗中，標記 [開發建置]**** 和 [指令碼偵錯]**** 核取方塊。

   ![設定用於偵錯的 Unity 組建設定。](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>選取要附加偵錯工具的 Unity 執行個體

- 在 Visual Studio 主功能表中，選擇 [偵錯] > [附加 Unity 偵錯工具]****。

   ![附加 Unity 的偵錯工具。](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   [選取 Unity 執行個體]**** 對話方塊會顯示您可連接之每個 Unity 執行個體的一些資訊。

   ![選擇要連接之 Unity 的執行個體。](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **專案**

   在這個 Unity 執行個體中執行的 Unity 專案名稱。

   **機器** 這個 Unity 執行個體執行所在的電腦或裝置名稱。

   如果這個 Unity 執行個體當做 Unity Editor 的一部分來執行，則為 **Type** **Editor**；如果這個 Unity 執行個體是獨立播放器，則為 **Player**。

   **連接埠** 這個 Unity 執行個體用於通訊之 UDP 通訊端的通訊埠編號。

> [!IMPORTANT]
> 由於 Visual Studio Tools for Unity 是透過 UDP 網路通訊端與 Unity 執行個體通訊，因此您的防火牆可能會要求這項資訊。 如果發生這種情況，您必須授權連接，VSTU 和 Unity 才能通訊。

### <a name="debug-a-dll-in-your-unity-project"></a>針對 Unity 專案中的 DLL 進行偵錯

許多 Unity 開發人員會將程式碼元件撰寫成外部 DLL，以便與其他專案共用他們所開發的功能。 Visual Studio Tools for Unity 可讓您順暢地連同 Unity 專案中的其他程式碼一起為這些 DLL 中的程式碼偵錯。

> [!NOTE]
> 目前，Visual Studio Tools for Unity 僅支援 Managed DLL， 並不支援對機器碼 DLL 進行偵錯 (例如以 C++ 撰寫的 DLL)。

請注意，此處所述的情節假設您有原始程式碼；也就是說，您正在開發或重複使用自己的第一方程式碼，或您有協力廠商程式庫的程式碼，並打算將其部署至 Unity 專案中做為 DLL。 該情節不會說明如何對您沒有原始程式碼的 DLL 進行偵錯。

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>為 Unity 專案所使用的 Managed DLL 專案偵錯

1. 將現有的 DLL 專案加入 Visual Studio Tools for Unity 所產生的 Visual Studio 方案。 在較不常見的情況下，您可能會啟動新的 Managed DLL 專案來包含 Unity 專案中的程式碼元件；如果是這種情況，您可以改為將新的 Managed DLL 專案加入 Visual Studio 方案。 如需將新的或現有的專案加入至方案的詳細資訊，請參閱[作法：將專案加入至方案](https://msdn.microsoft.com/library/ff460187.aspx)。

   ![將現有的 DLL 專案加入方案。](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   不論是哪一種情況，Visual Studio Tools for Unity 都會保留專案參考 (即使必須再次重新產生專案和方案檔亦然)，因此您只需要執行這些步驟一次。

2. 參考 DLL 專案中的正確 Unity Framework 設定檔。 在 Visual Studio 的 DLL 專案屬性中，將 [目標 Framework]**** 屬性設定為您所使用的 Unity Framework 版本。 這是與專案的目標應用程式開發介面相容的 Unity 基底類別庫，例如 Unity 完整、微型或 Web 基底類別庫。 如此可防止 DLL 呼叫存在於其他 Framework 或相容性層級中，但可能不存在於您所使用之 Unity Framework 版本的 Framework 方法。

> [!NOTE]
> 僅在使用 Unity 的舊版執行階段時才需要以下內容。 如果您使用的是新的 Unity 執行階段，則不再需要使用這些專用的 3.5 設定檔。 使用與 Unity 版本相容的 .NET 4.x 設定檔。

   ![DLL 的目標架構設定為 Unity 架構。](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. 將 DLL 複製到 Unity 專案的 Assets 資料夾。 在 Unity 中，資產是與 Unity 應用程式一起封裝及部署的檔案，以便可以在執行階段載入。 由於 DLL 在運行時連結,因此必須將 DLL 部署為資產。 為了將 DLL 部署為資產，Unity Editor 會要求將 DLL 放在 Unity 專案的 [Assets] 資料夾中。 有兩種方式可讓您完成這個步驟：

   - 修改 DLL 專案的組建設定，以包含將輸出 DLL 和 PDB 檔案從其輸出資料夾複製到 Unity 專案之 [Assets]**** 資料夾的建置後工作。

   - 修改 DLL 專案的組建設定，將其輸出資料夾設定為 Unity 專案的 [Assets]**** 資料夾。 DLL 和 PDB 檔案都會被放在 [Assets]**** 資料夾中。

   由於 PDB 檔案包含 DLL 的偵錯符號，並將 DLL 程式碼對應至其原始程式碼形式，因此偵錯時會需要這些檔案。 如果您是以舊版執行階段為目標，Visual Studio Tools for Unity 將會使用 DLL 和 PDB 中的資訊來建立 DLL.MDB 檔案，這是舊版 Unity 指令碼引擎所使用的偵錯符號格式。 如果您是以新的執行階段為目標，並使用可攜式 PDB，則 Visual Studio Tools for Unity 將不會嘗試執行任何的符號轉換，因為新的 Unity 執行階段是以原生方式使用可攜式 PDB。

   有關產生 PDB 的更多資訊，請參閱[此處](../debugger/how-to-set-debug-and-release-configurations.md)。 如果您是以新的執行階段為目標，請確定 [偵錯資訊] 設定為 [可攜式]，以便正確地產生可攜式 PDB。 如果您是以舊版執行階段為目標，則需要使用 [完整]。

4. 為程式碼偵錯。 您現在可以連同 Unity 專案的原始程式碼一起為 DLL 原始程式碼偵錯，並使用您慣用的所有偵錯功能，例如中斷點和逐步執行程式碼。

## <a name="keyboard-shortcuts"></a>鍵盤快速鍵

您可以使用鍵盤快速鍵快速存取 Unity Tools for Visual Studio 功能。 以下是可用的快速鍵摘要。

|Command|快速鍵|快速鍵命令名稱|
|-------------|--------------|---------------------------|
|開啟 MonoBehavior 精靈|**Ctrl**+**換檔**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|開啟 Unity Project Explorer|**Alt**+**移位**+**元 E**|**View.UnityProjectExplorer**|
|存取 Unity 文件|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|附加至 Unity 偵錯工具 (播放器或編輯器)|**_沒有預設值_**|**Debug.AttachUnityDebugger**|

如果您不喜歡預設值，可以變更快速鍵組合。 如需如何變更它的詳細資訊，請參閱[識別及自訂 Visual Studio 中的鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。
