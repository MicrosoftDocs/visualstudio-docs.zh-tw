---
title: "JIT 最佳化和偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 23de1ec4e053a87c4f91cf7b599f49b8fe318015
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="jit-optimization-and-debugging"></a>JIT 最佳化和偵錯
**最佳化在.NET 中的運作方式：**如果您嘗試偵錯程式碼，很容易當程式碼是**不**最佳化。 這是因為當程式碼已最佳化，編譯器和執行階段變更發出的 CPU 程式碼，讓執行速度較快，但較不直接對應到原始的原始程式碼。 這表示偵錯工具會經常無法告訴您的本機變數的值，以及逐步執行程式碼，而且中斷點可能不會如預期般運作。

通常會發行組建組態建立最佳化的程式碼和偵錯組建組態並不會。 `Optimize` MSBuild 屬性控制是否告知編譯器最佳化程式碼。

.NET 生態系統中的程式碼已從來源中兩步驟程序的 CPU 指示： C# 編譯器首先，將您輸入的文字轉換成呼叫 MSIL 中繼二進位格式，並寫出此.dll 檔案。 更新版本中，.NET 執行階段會將此 MSIL 轉換成 CPU 指示。 這兩個步驟可以最佳化某種程度上，但是.NET 執行階段所執行的第二個步驟會執行更重要的最佳化。

**'隱藏 JIT 最佳化 (僅限 Managed) 的模組載入' 選項：**偵錯工具會公開控制目標處理序內載入的 DLL，以啟用最佳化編譯時，會發生什麼情況的選項。 如果未選取此選項 （預設狀態），則如果.NET 執行階段將 MSIL 程式碼編譯成 CPU 程式碼中，它會將保持啟用最佳化。 如果勾選此選項，偵錯工具要求會以停用最佳化。

**(僅限 Managed) 的模組載入時隱藏 JIT 最佳化**選項可以找到上**一般**頁面**偵錯**節點**選項**  對話方塊。

**何時應該檢查此選項：**核取此選項，當您從其他來源，例如 nuget 套件，下載 Dll，而且您想要偵錯這個 DLL 中的程式碼。 為了讓此工作，您也必須針對此 DLL 尋找符號 (.pdb) 檔。

如果您只想要偵錯在本機建置的程式碼，所以最好將此選項保持未核取，因為在某些情況下，啟用此選項將會大幅減慢偵錯。 有速度變慢的兩個原因：

* 最佳化程式碼執行速度。 如果許多程式碼的最佳化會關閉，對效能的影響可以加總。
* 如果您有啟用 Just My Code，偵錯工具將甚至不能再試一次，並載入符號的 Dll，最佳化。 尋找符號可能需要很長的時間。

**這個選項的限制：**有兩種情況，這個選項會在哪裡**不**運作：

1. 在您會將偵錯工具附加至正在執行的處理序的情況下，此選項，就可以在已附加偵錯工具已經載入的模組不會影響。
2. 這個選項沒有任何作用，dll 已預先編譯的原生程式碼 (又稱為 ngen)。 不過，您可以使用環境變數 'COMPlus_ZapDisable' 設為 '1' 啟動處理序來停用預先編譯的程式碼的使用方式。

## <a name="see-also"></a>請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [使用偵錯工具巡覽程式碼](../debugger/navigating-through-code-with-the-debugger.md)   
 [附加至執行中處理程序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Managed 執行程序](/dotnet/standard/managed-execution-process)
