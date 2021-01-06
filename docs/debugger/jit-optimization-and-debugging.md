---
title: JIT 優化和調試 |Microsoft Docs
description: 優化的程式碼比非程式碼更難進行比對。 瞭解 JIT 優化，以及何時及如何將它隱藏。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66f63c7232b52ebe849722147e007ab70527c311
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903918"
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
如果您想要進行程式碼的偵錯工具，則在該程式碼 **未** 優化的情況下會比較容易。 當程式碼優化時，編譯器和執行時間會變更發出的 CPU 程式碼，使其執行速度更快，但不會直接對應至原始原始程式碼。 如果對應較不直接，則偵錯工具通常無法告訴您區域變數的值，而且程式碼逐步執行和中斷點可能無法如您預期般運作。

> [!NOTE]
> 如需 JIT (即時) 偵錯工具的詳細資訊，請閱讀 [本檔](../debugger/debug-using-the-just-in-time-debugger.md)。

## <a name="how-optimizations-work-in-net"></a>.NET 中的優化運作方式 
發行組建設定通常會建立優化的程式碼，而 Debug 組建設定則否。 `Optimize`MSBuild 屬性會控制是否指示編譯器將程式碼優化。

在 .NET 生態系統中，程式碼會以兩個步驟的程式從來源轉換為 CPU 指示：首先，c # 編譯器會將您輸入的文字轉換為中繼二進位格式（稱為 MSIL），並將 MSIL 寫入 .dll 檔案。 之後，.NET 執行時間會將此 MSIL 轉換為 CPU 指令。 這兩個步驟都可以優化至某種程度，但 .NET 執行時間所執行的第二個步驟會執行更多的優化。

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>[模組載入時隱藏 JIT 優化 (僅限 Managed) ] 選項
偵錯工具會公開一個選項，以控制在目標進程內已啟用優化的 DLL 載入時，會發生什麼事。 如果未核取此選項 (預設狀態) ，則當 .NET 執行時間將 MSIL 程式碼編譯為 CPU 程式碼時，就會讓優化保持啟用狀態。 如果選取此選項，則偵錯工具會要求停用優化。

若要 **在模組載入 ([僅限 Managed])** 選項中尋找 [隱藏 JIT 優化] 選項，請選取 [**工具**  >  **選項**]，然後選取 [**調試**] 節點下的 **[一般**] 頁面。

![隱藏 JIT 優化](../debugger/media/suppress-jit-tool-options.png "隱藏 JIT 優化")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>何時應該選取 [隱藏 JIT 優化] 選項？
當您從另一個來源下載 Dll （例如 nuget 套件），而且想要在此 DLL 中進行程式碼的偵錯工具時，請選取此選項。 為了讓隱藏專案正常運作，您也必須尋找此 DLL ( .pdb) 檔的符號。

如果您只想要對要在本機建立的程式碼進行偵錯工具，最好不要勾選這個選項，因為在某些情況下，啟用此選項將會大幅降低偵錯工具的速度。 這種緩慢的原因有兩個：

* 優化的程式碼執行速度更快。 如果您要關閉許多程式碼的優化，可能會增加效能影響。
* 如果您已啟用 Just My Code，則偵錯工具甚至不會嘗試載入已優化 Dll 的符號。 尋找符號可能需要很長的時間。

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>[隱藏 JIT 優化] 選項的限制 
開啟此選項的情況有兩種： 

1. 當您將偵錯工具附加至已在執行中的進程時，這個選項不會影響已在附加偵錯工具時載入的模組。
2. 此選項不會影響已預先編譯 (ngen) 至機器碼的 Dll。 不過，您可以啟動程式，將環境變數 **' COMPlus_ReadyToRun '** 設定為 **' 0 '**，以停用預先編譯器代碼的使用方式。 這會指示 .NET Core 執行時間停用預先編譯的影像，並強制執行時間進行 JIT 編譯架構程式碼。 

    > [!IMPORTANT]
    > 如果您的目標是 .NET Framework 或舊版的 .NET Core (2.x 或更低的) ，也請新增環境變數 ' COMPlus_ZapDisable ' 並將它設定為 ' 1 '

    **若要在 Visual Studio 中設定 .NET Core 專案的環境變數：**
    1. 在 [ **方案總管** 中，以 **滑鼠右鍵按一下** 專案檔，然後選取 [ **屬性**]。
    2. 流覽至 [ **調試** ] 索引標籤，然後按一下 [ **環境變數**] 下的 [ **加入** ] 按鈕。
    3. 將 [名稱] (索引鍵) 設定為 **COMPlus_ReadyToRun** ，並將值設定為 **0**。

    ![設定 COMPlus_ReadyToRun 環境變數](../debugger/media/environment-variables-debug-menu.png "設定 COMPlus_ReadyToRun 環境變數")

## <a name="see-also"></a>另請參閱
- [如何調試 Dotnet Framework 來源](../debugger/how-to-debug-dotnet-framework-source.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)
- [附加到正在執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Managed 執行進程](/dotnet/standard/managed-execution-process)
