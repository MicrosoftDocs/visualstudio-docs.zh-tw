---
title: 將 GPU 程式碼進行偵錯工具 |Microsoft Docs
description: 瞭解 Visual Studio 中 (GPU) 在圖形處理器上執行的 c + + 程式碼的偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19191d8d46e17da52b13f692db605168b06b38d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872673"
---
# <a name="debugging-gpu-code"></a>偵錯 GPU 程式碼
您可以對圖形處理器 (GPU) 上執行的 C++ 程式碼進行偵錯。 在 Visual Studio 中的 GPU 偵錯支援包括競爭偵測、啟動處理序和附加至處理序，以及整合到偵錯視窗中。

## <a name="supported-platforms"></a>支援的平台
 [!INCLUDE[win7](../debugger/includes/win7_md.md)]、 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 、Windows 10、 [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] 和 Windows Server 2016 支援偵錯工具。 若要在軟體模擬器、、Windows 10 或上進行偵錯工具， [!INCLUDE[win8](../debugger/includes/win8_md.md)] [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] 則需要 Windows Server 2016。 如需在硬體上偵錯，您必須安裝圖形卡的驅動程式。 並非所有硬體廠商都實作所有偵錯工具功能。 請參閱廠商文件以了解限制。

> [!NOTE]
> 若獨立硬體廠商想要支援 Visual Studio 中的 GPU 偵錯，則必須建立實作 VSD3DDebug 介面並且以自己的驅動程式為目標的 DLL。

## <a name="configuring-gpu-debugging"></a>設定 GPU 偵錯
 偵錯工具無法在相同應用程式執行時中斷 CPU 程式碼和 GPU 程式碼。 根據預設，偵錯工具會中斷 CPU 程式碼。 若要對 GPU 程式碼進行偵錯，請使用這兩個步驟的其中一個：

- 在 [標準] 工具列的 [偵錯類型] 清單中，選擇 [僅限 GPU]。

- 在 [方案總管] 中，在專案的捷徑功能表上選擇 [屬性]。 在 [屬性頁] 對話方塊中，選取 [偵錯]，然後在 [偵錯工具類型] 清單中選取 [僅限 GPU]。

## <a name="launching-and-attaching-to-applications"></a>啟動和附加至應用程式
 您可以使用 Visual Studio 偵錯命令啟動和停止 GPU 偵錯。 如需詳細資訊，請參閱[使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)。 您也可以將 GPU 偵錯工具附加至執行中的處理序，但是只有在該處理序執行 GPU 程式碼時才能這樣做。 如需詳細資訊，請參閱 [附加至正在](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)執行的進程。

## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>執行目前 Tile 至游標處和執行至游標處
 在 GPU 上偵錯時，您有兩個選項可以執行至游標位置。 這兩個選項的命令可從程式碼編輯器的捷徑功能表使用。

1. [執行至游標處] 命令會執行應用程式，直到其到達游標位置，然後中斷。 這並不表示目前執行緒會執行至游標處，而是表示到達游標位置的第一個執行緒觸發中斷。 請參閱 [使用偵錯工具流覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)

2. [執行目前 Tile 至游標處] 命令會執行應用程式，直到目前 Tile 中的所有執行緒到達游標處，然後中斷。

## <a name="debugging-windows"></a>偵錯視窗
 您可以使用某些偵錯視窗檢查和凍結 GPU 執行緒，以及為它們加上旗標。 如需詳細資訊，請參閱

- [使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md)

- [使用工作視窗](../debugger/using-the-tasks-window.md)

- [如何：使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)

- 偵錯工具[執行緒和進程](../debugger/debug-threads-and-processes.md) (偵錯工具位置工具列) 

- [如何：使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)

## <a name="data-synchronization-exceptions"></a>資料同步處理的例外狀況
 偵錯工具可能在執行期間識別出幾個資料同步處理的情況。 當偵測到某種情況時，偵錯工具就會進入中斷模式。 有兩個選項可供您使用：[中斷] 或 [繼續]。 使用 [例外狀況] 對話方塊可以設定偵錯工具是否要偵測這些情況，以及要針對哪些情況中斷。 如需詳細資訊，請參閱 [使用偵錯工具管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況。 您也可以使用 [選項] 對話方塊指定如果寫入的資料不會變更資料值，則偵錯工具應該忽略例外狀況。 如需詳細資訊，請參閱 [General, Debugging, Options Dialog Box](../debugger/general-debugging-options-dialog-box.md)。

## <a name="troubleshooting"></a>疑難排解

### <a name="specifying-an-accelerator"></a>指定加速器
 GPU 程式碼中的中斷點只有在程式碼在 [accelerator::direct3d_ref](/cpp/parallel/amp/reference/accelerator-class#direct3d_ref) (REF) 加速器上執行時才會叫用。 如果您未在程式碼中指定加速器，則會在專案屬性中自動選取 REF 加速器作為 [偵錯加速器類型]。 如果您的程式碼明確選取加速器，則不會在偵錯期間使用 REF 加速器，而且除非您的 GPU 硬體支援偵錯，否則不會叫用中斷點。 您可以撰寫自己的程式碼補救這種情況，讓程式碼在偵錯期間使用 REF 加速器。 如需詳細資訊，請參閱專案屬性和使用快速鍵，以及[c + + 偵錯工具](../debugger/project-settings-for-a-cpp-debug-configuration.md)的[Accelerator_view 物件](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects)和專案設定。

### <a name="conditional-breakpoints"></a>條件中斷點
 GPU 程式碼支援條件中斷點，不過，並非所有運算式都可以在裝置上進行評估。 如果運算式無法在裝置上評估，就會在偵錯工具上評估。 偵錯工具的執行速度可能會比裝置更慢。

### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>錯誤：選取的偵錯加速器類型發生設定問題。
 如果專案設定和您進行偵錯所在電腦的組態不一致，就會發生這個錯誤。 如需詳細資訊，請參閱 [c + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。

### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>錯誤：選取的偵錯加速器類型的偵錯驅動程式未安裝在目標電腦上。
 如果您是在遠端電腦上進行偵錯，就會發生這個錯誤。 在執行階段之前，偵錯工具無法判斷驅動程式是否安裝在遠端電腦上。 驅動程式可向圖形卡的製造商取得。

### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>錯誤：遠端網站必須停用「逾時偵錯與復原」(TDR)。
 C++ AMP 計算可能會超過 Windows 逾時偵測與復原程序 (TDR) 所設定的預設時間間隔。 發生這種情況時，計算就會取消，而且資料將會遺失。 如需詳細資訊，請參閱 [Handling TDRs in C++ AMP](/archive/blogs/nativeconcurrency/handling-tdrs-in-c-amp) (在 C++ AMP 中處理 TDR)。

## <a name="see-also"></a>另請參閱
- [逐步解說： C++ AMP 應用程式的偵錯工具](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)
- [C + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [在 Visual Studio 中開始 GPU 偵錯](/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)