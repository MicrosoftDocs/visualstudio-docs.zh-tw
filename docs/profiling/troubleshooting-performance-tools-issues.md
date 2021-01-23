---
title: 效能工具問題疑難排解 | Microsoft Docs
description: 瞭解當您針對效能工具問題進行疑難排解時，可能會遇到的各種問題，例如，程式碼剖析工具未收集資料時。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d079c2fbd41f6a3eff881a544e8b88c50938e3bf
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722408"
---
# <a name="troubleshoot-performance-tools-issues"></a>針對效能工具問題進行疑難排解
當您使用程式碼剖析工具時，可能會遇到下列其中一個問題：

- [程式碼剖析工具沒有收集到任何資料](#no-data-is-collected-by-the-profiling-tools)

- [效能檢視和報表將函式名稱顯示為數字](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>程式碼剖析工具沒有收集到任何資料
 在您分析應用程式之後，並未建立程式碼剖析資料 (.*vsp*) 檔案，而且您在 [輸出] 視窗或命令視窗中收到下列警告：

 PRF0025: 未收集任何資料。

 有幾個問題會造成這個問題︰

- 使用取樣或 .NET 記憶體方法分析的處理序，啟動的子處理序會成為執行應用程式工作的處理序。 例如，一些應用程式會讀取該命令列，判斷其要啟動為 Windows 應用程式或命令列應用程式。 如果要求 Windows 應用程式時，原始的處理序會啟動設定為 Windows 應用程式的新處理序，然後結束原始的處理序。 因為程式碼剖析工具不會自動收集子處理序的資料，所以不會收集到任何資料。

     若要在這種情況下收集程式碼剖析資料，請將分析工具附加至子處理序，而不是使用分析工具來啟動應用程式。 如需詳細資訊，請參閱[如何：為執行中的處理序附加和中斷連結效能工具](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)和[附加 (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>效能檢視和報表將函式名稱顯示為數字
 在您分析應用程式之後，您在報表和檢視中看到數字，而不是函式名稱。

 這是由程式碼剖析工具分析引擎造成的問題，因其無法找到其所含的符號資訊與原始程式碼資訊對應的 .*pdb* 檔，例如已編譯檔案的函式名稱和行號。 根據預設，編譯器會在建置應用程式檔案時建立 .*pdb* 檔。 .*pdb* 檔案的本機目錄參考會儲存在已編譯的應用程式中。 分析引擎會在參考的目錄中尋找 .*pdb* 檔，然後在目前包含應用程式檔案的檔案中尋找。 如果找不到 .*pdb* 檔，分析引擎會使用函式位移，而不是函式名稱。

 您可以下列兩種方式解決這個問題︰

- 找到 .*pdb* 檔，並放入和應用程式檔案相同的目錄。

- 在程式碼剖析資料 (.*vsp*) 檔案中內嵌符號資訊。 如需詳細資訊，請參閱[使用效能資料檔案儲存符號資訊](../profiling/saving-symbol-information-with-performance-data-files.md)。

> [!NOTE]
> 分析引擎所需的 .*pdb* 檔版本要和編譯的應用程式檔案相同。 來自舊版或更新版本的應用程式檔案的 .*pdb* 檔不適用。
