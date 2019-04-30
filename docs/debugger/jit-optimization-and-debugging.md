---
title: JIT 最佳化和偵錯 |Microsoft Docs
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
ms.openlocfilehash: 7346b6fd8fbd483021437638f9e134ead88a0b93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846319"
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
**如何最佳化會在.NET 中運作：** 如果您嘗試偵錯程式碼，這遠時，程式碼是**不**最佳化。 這是因為當程式碼最佳化時，編譯器和執行階段發出 CPU 程式碼進行變更，讓它執行速度較快，但較不直接對應至原始的原始程式碼。 這表示偵錯工具會經常無法告訴您的本機變數的值，然後逐步執行程式碼，而且中斷點可能無法如預期運作。

通常 [發行] 組建組態建立最佳化的程式碼，並偵錯組建組態並不會。 `Optimize` MSBuild 屬性可讓您控制是否告知編譯器最佳化程式碼。

是.NET 生態系統中，程式碼會變成從來源中的兩步驟程序的 CPU 指令： 首先，C#編譯器將您輸入的文字轉換成稱為 MSIL 中繼二進位格式，並寫出此.dll 檔案。 更新版本中，.NET 執行階段會將此 MSIL 轉換為 CPU 指令。 這兩個步驟可以最佳化某種程度上，但是.NET 執行階段所執行的第二個步驟會執行更大量的最佳化。

**[隱藏 JIT 最佳化模組載入 （僅限受控）] 選項中：** 偵錯工具會公開一個選項，以啟用最佳化編譯的 DLL 載入目標處理序內時，會發生什麼事的控制。 如果未選取此選項 （預設狀態），則當.NET 執行階段會將 MSIL 程式碼編譯成 CPU 程式碼，將會使啟用最佳化。 如果勾選此選項，則偵錯工具要求會以停用最佳化。

若要尋找**隱藏 JIT 最佳化 （僅限受控） 的模組載入**選項中，選取**工具** > **選項**，然後選取  **一般**頁面**偵錯**節點。

**當您應該選取此選項：** 當您從其他來源，例如 nuget 套件，下載 Dll，而且您想要偵錯這個 DLL 中的程式碼時，請核取此選項。 為了讓此做法能夠運作，您也必須尋找符號 (.pdb) 檔案。 這個 DLL。

如果您只想要偵錯您要在本機建置的程式碼，最好是核取此選項，因為在某些情況下，啟用此選項會大幅減慢偵錯。 有速度變慢的兩個原因如下：

* 最佳化程式碼執行速度較快。 如果您會關閉最佳化程式碼的多個，最多可新增的效能影響。
* 如果您有啟用 Just My Code，偵錯工具甚至不會嘗試和最佳化 dll 載入符號。 尋找符號可能需要很長的時間。

**這個選項的限制：** 有兩種情況，此選項會在哪裡**不**運作：

1. 在其中您要在這裡將偵錯工具附加至執行中程序的情況下，此選項不會影響在已附加偵錯工具已經載入的模組。
2. 這個選項沒有任何作用，於 Dll 已先行編譯的原生程式碼 (又稱為 ngen)。 不過，您可以將環境變數 'COMPlus_ZapDisable' 設定為 '1' 啟動程序來停用預先編譯的程式碼的使用方式。

## <a name="see-also"></a>另請參閱
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)
- [附加到執行中的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Managed 執行程序](/dotnet/standard/managed-execution-process)
