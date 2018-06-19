---
title: 疑難排解和已知問題 (Visual Studio Tools for Unity) | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cb1da2ec2c41fcbec78864868d116bcd1684a5b2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562009"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>疑難排解和已知問題 (Visual Studio Tools for Unity)
在本節中，您將找到 Visual Studio Tools for Unity 之常見問題的解決方法、已知問題的描述，並了解如何透過回報錯誤來協助改善 Visual Studio Tools for Unity。

## <a name="troubleshooting"></a>疑難排解
若要解決 Visual Studio Tools for Unity 的一些常見問題，請參閱下列各節。

### <a name="visual-studio-crashes"></a>Visual Studio 當機
這可能是因為 Visual Studio 的 MEF 快取損毀所致。

您應該移除下列資料夾以重設 MEF 快取 (請先關閉 Visual Studio 再執行這項操作)：

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

這麼做應該可以修正您的問題。 如果仍然遇到問題，請以系統管理員身分執行 Visual Studio 的開發人員命令提示字元，然後使用下列命令：

```batch
 devenv /setup
```

### <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Visual Studio 2015 和 IntelliSense 或程式碼色彩的問題。
您應該嘗試將 Visual Studio 2015 升級至 Update 3。

### <a name="shader-files-without-code-coloration-when-using-visual-studio-2017"></a>使用 Visual Studio 2017 時著色器檔案無程式碼著色
請確定您的 Visual Studio 2017 執行個體已安裝「使用 C++ 開發桌面」工作負載。 用於程式碼著色的 C/C++ 剖析器隨附於此工作負載。

### <a name="visual-studio-hangs"></a>Visual Studio 停止回應
剖析、FMOD、UMP (通用媒體播放程式)、ZFBrowser 或 Embedded Browser 這類 Unity 外掛程式會使用原生執行緒。 但當外掛程式最後將原生執行緒附加到執行階段時則會發生問題，因為這會導致作業系統的呼叫受到封鎖。 這表示 Unity 無法為偵錯工具中斷該執行緒 (或網域重新載入)，因此會停止回應。

針對 FMOD，有下列因應措施：您可以傳遞 FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE 初始化[旗標](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html)以停用非同步處理，並在主執行緒上執行所有處理。

### <a name="incompatible-project-in-visual-studio"></a>Visual Studio 中的不相容專案
首先，檢查 Unity 中是否已將 Visual Studio 設定為您的外部指令碼編輯器 ([編輯]/[喜好設定]/[外部工具])。 然後，檢查 Unity 外掛程式中是否已安裝 Visual Studio  ([說明]/[關於] 底部必須顯示一則類似 Microsoft Visual Studio Tools for Unity 已啟用的訊息)。 接著，檢查 Visual Studio 中是否已正確安裝延伸模組 ([說明]/[關於])。

### <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>額外重新載入，或 Visual Studio 遺失所有開啟的視窗
請務必不要再直接從資產處理器或任何其他工具處理專案檔。 如果您真的需要操作專案檔，我們會公開它的 API。 請參閱[組件參考問題](#Assembly-reference-issues)一節。

如果您發生額外重新載入，或如果 Visual Studio 在重新載入中遺失所有開啟的視窗，請確定您安裝了正確的 .NET 目標套件。 如需架構的詳細資訊，請參閱下節。

###  <a name="the-debugger-does-not-break-on-exceptions"></a>偵錯工具不會因例外狀況而中斷
使用舊版的 Unity 執行階段 (.NET 3.5 對等項目) 時，偵錯工具一律會在例外狀況未處理時 (= 在 try/catch 區塊之外) 時中斷。 如已處理例外狀況，偵錯工具就會使用 [例外狀況設定] 視窗判斷是否有必要中斷。

使用新的執行階段 (.NET 4.6 對等項目)，Unity 推出管理使用者例外狀況的新方法，結果讓所有的例外狀況都被視為「使用者已處理」，即使它們是在 try/catch 區塊之外。 這就是為什麼如果您現在想要中斷偵錯工具，就需要在 [例外狀況設定] 視窗中明確勾選它們。

在 [例外狀況設定] 視窗中 ([偵錯] > [Windows] > [例外狀況設定])，展開例外狀況分類節點 (例如，表示.NET 例外狀況的 [Common Language Runtime 例外狀況])，並選取要在該分類內擷取的特定例外狀況核取方塊 (例如 System.NullReferenceException)。 您也可以選取例外狀況的整個類別。

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>使用 Windows 時，Visual Studio 會要求下載 Unity 目標 Framework
Visual Studio Tools for Unity 需要 .NET Framework 3.5，但 Windows 8 或 Windows 10 上預設為未安裝。 若要修正這個問題，請遵循指示下載並安裝 .Net Framework 3.5。

使用新的 Unity 執行階段時，也需要 .NET 以 4.6 和 4.7.1 版的組件為目標。 使用 VS2017 安裝程式有可能快速安裝它們 (修改您的 VS2017 安裝、個別元件、.NET 分類、選取所有 4.x 目標組件)。

### <a name="assembly-reference-issues"></a>組件參考問題
如果您的專案參考很複雜，或您想更妥善控制這個產生步驟，則可以使用我們的 [API](../cross-platform/customize-project-files-created-by-vstu.md) 來操作產生的專案或方案內容。 您也可以在 Unity 專案中使用[回應檔](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)，我們即會進行處理。

### <a name="breakpoints-with-a-warning"></a>中斷點與警告
如果 Visual Studio 找不到特定中斷點的來源位置，中斷點周圍即會顯示警告。 請檢查您正在使用的行為是否已正確載入/用於目前的 Unity 場景中。

### <a name="breakpoints-not-hit"></a>未達到的中斷點
請檢查您正在使用的行為是否已正確載入/用於目前的 Unity 場景中。 結束 Unity 和 Visual Studio，然後刪除所有產生的檔案 (*.csproj、*.sln) 和整個文件庫資料夾。

### <a name="unable-to-attach"></a>無法附加
-   請嘗試暫時停用您的防毒軟體，或為 VS 和 Unity 建立排除規則。
-   請嘗試暫時停用防火牆，或建立規則以允許 VS 與 Unity 之間的 TCP/UDP 網路功能。
-   我們發現 Team Viewer 這類程式會干擾處理序偵測；您或許可以嘗試暫時停止任何額外的軟體，看看是否有什麼變化。
-   因為 VSTU 只會監視 "Unity.exe" 處理序，所以請不要重新命名主要 Unity 可執行檔。

### <a name="unable-to-debug-android-players"></a>無法偵錯 Android 播放器
我們使用多點傳送進行播放器偵測 (這是 Unity 所使用的預設機制)，在此之後，我們會使用一般的 TCP 連線來附加偵錯工具。 對 Android 裝置來說，偵測階段是 主要問題。

WiFi 很靈活，但因為延遲，所以相較於 USB 速度超慢。 我們發現針對某些路由器或裝置 (Nexus 系列是其中的已知裝置) 缺乏適當的多點傳送支援。

USB 偵錯的速度超快，而且 Visual Studio Tools for Unity 現已可偵測 USB 裝置，與 adb 伺服器通訊以正確轉送連接埠來進行偵錯。

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>從 UnityVS 移轉至 Visual Studio Tools for Unity
 如果您要從 UnityVS 移轉至 Visual Studio Tools for Unity，您必須為 Unity 專案產生新的 Visual Studio 方案。

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>將 Unity 專案從 UnityVS 1.8 移轉至 Visual Studio Tools for Unity 1.9

1.  從您的 Unity 專案中刪除舊的方案和專案檔。 在您的 Unity 專案根目錄中，找出並刪除所有 Visual Studio .sln 和 .*proj 檔。

2.  將 Visual Studio Tools for Unity 套件匯入 Unity 專案。 如需如何匯入 VSTU 套件的相關資訊，請參閱 [使用者入門](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) 頁面上的＜設定 Visual Studio Tools for Unity＞。

3.  產生新的方案和專案檔。 如果您想要立即產生檔案，請在 Unity Editor 主功能表上，選擇 [Visual Studio Tools] 、[Generate Project Files] 。 否則，您可以視需要略過這個步驟；當您選擇 [Visual Studio Tools] 、[Open in Visual Studio] 時，Visual Studio Tools for Unity 會自動產生新檔案。

## <a name="known-issues"></a>已知問題
 Visual Studio Tools for Unity 在偵錯工具如何與 Unity 的舊版 C# 編譯器互動方面有已知問題。 我們正在努力協助修正這些問題，在此同時，您可能會遇到下列問題：

-   偵錯時，Unity 有時會損毀。

-   偵錯時，Unity 有時會凍結。

-   逐步執行和跳離方法有時運作異常，尤其是在 iterator 或 switch 陳述式內。

## <a name="reporting-errors"></a>報告錯誤
 當您遇到損毀、凍結或其他錯誤時，請傳送錯誤報告，以協助我們改善 Visual Studio Tools for Unity 的品質。 這可協助我們調查並修正 Visual Studio Tools for Unity 的問題。 感謝您！

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>如何在 Visual Studio 凍結時回報錯誤
 根據報告，當使用 Visual Studio Tools for Unity 進行偵錯時，Visual Studio 有時會凍結，不過我們需要更多資料來了解這個問題。 您可以執行下列步驟來協助我們進行調查。

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>回報使用 Visual Studio Tools for Unity 進行偵錯時 Visual Studio 凍結的情形

*在 Windows 上*：

1.  開啟新的 Visual Studio 執行個體。

2.  開啟 [附加至處理序] 對話方塊。 在新的 Visual Studio 執行個體的主功能表上，選擇 [偵錯] 、[附加至處理序] 。

3.  將偵錯工具附加至 Visual Studio 的已凍結執行個體。 在 [附加至處理序]  對話方塊中，從 [可使用的處理序]  資料表選取 Visual Studio 的已凍結執行個體，然後選擇 [附加]  按鈕。

4.  暫停偵錯工具。 在 Visual Studio 新執行個體的主功能表上，選擇 [偵錯]、[全部中斷]，或直接按 **Ctrl+Alt+Break**。

5.  建立執行緒傾印。 在命令視窗中輸入下列命令，然後按 **Enter** 鍵：

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    您可能需要先顯示 [命令]  視窗。 在 Visual Studio 主功能表上，選擇 [檢視] 、[其他視窗] 、[命令視窗] 。

*在 Mac 上*：

1. 開啟終端機，並取得 Visual Studio for Mac 的 PID：

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. 啟動 lldb 偵錯工具：

    ```shell
    lldb
    ```

1. 使用 PID 附加至 Visual Studio for Mac 的執行個體：

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. 擷取所有執行緒的堆疊追蹤：

    ```shell
    bt all
    ```

最後，將執行緒傾印傳送至 [vstusp@microsoft.com](mailto:vstusp@microsoft.com)，並提供您在 Visual Studio 變成凍結時所執行的動作描述。
