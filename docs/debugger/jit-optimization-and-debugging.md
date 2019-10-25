---
title: JIT 優化和調試 |Microsoft Docs
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
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731628"
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
**優化在 .net 中的工作方式：** 如果您嘗試進行程式碼的偵錯工具，當該程式碼**未**優化時，會比較容易。 這是因為當程式碼優化時，編譯器和執行時間會對發出的 CPU 程式碼進行變更，使其執行速度較快，但對原始原始程式碼的直接對應較少。 這表示偵錯工具經常無法告訴您本機變數的值，而且程式碼逐步執行和中斷點可能無法如預期般運作。

通常，發行組建設定會建立優化的程式碼，而 Debug 組建設定則不會。 @No__t_0 MSBuild 屬性會控制編譯器是否已被告知優化程式碼。

在 .NET 生態系統中，程式碼會在兩個步驟的程式中從來源轉換為 CPU 指示： C#首先，編譯器會將您輸入的文字轉換成稱為 MSIL 的中繼二進位格式，並將此內容寫出至 .dll 檔案。 之後，.NET 執行時間會將此 MSIL 轉換為 CPU 指令。 這兩個步驟都可以優化到某種程度，但 .NET 執行時間所執行的第二個步驟會執行更重要的優化。

**[模組載入時隱藏 JIT 優化（僅限 Managed）] 選項：** 偵錯工具會公開一個選項，控制在目標進程內以優化方式啟用的 DLL 編譯時，會發生什麼事。 如果未核取此選項（預設狀態），則當 .NET 執行時間將 MSIL 程式碼編譯成 CPU 程式碼時，它會讓優化保持啟用狀態。 如果已核取此選項，則偵錯工具會要求停用優化。

若要尋找 **模組載入時隱藏 JIT 優化（僅限 Managed）**  選項，請選取 **工具**  > **選項**，然後選取 **調試** 節點底下的 **一般** 頁面。

**何時應該勾選此選項：** 當您從另一個來源（例如 nuget 套件）下載 Dll，而且想要在此 DLL 中進行程式碼的偵錯工具時，請核取此選項。 為了讓此作業正常，您也必須尋找此 DLL 的符號（.pdb）檔案。

如果您只想要對您在本機上建立的程式碼進行偵錯工具，最好不要核取此選項，在某些情況下，啟用此選項會大幅降低偵錯工具的速度。 此速度變慢的原因有兩個：

* 優化程式碼的執行速度較快。 如果您要關閉許多程式碼的優化，可能會增加效能影響。
* 如果您已啟用 Just My Code，偵錯工具甚至不會針對已優化的 Dll 嘗試和載入符號。 尋找符號可能需要很長的時間。

**此選項的限制：** 在兩種情況下，此選項將**無法**使用：

1. 在您將偵錯工具附加至已在執行中的進程時，這個選項不會影響已在附加偵錯工具時載入的模組。
2. 這個選項不會影響已預先編譯（ngen）至機器碼的 Dll。 不過，您可以藉由啟動程式並將環境變數 ' COMPlus_ZapDisable ' 設定為 ' 1 '，來停用預先編譯器代碼的使用方式。

## <a name="see-also"></a>請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)
- [附加到執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Managed 執行程序](/dotnet/standard/managed-execution-process)
