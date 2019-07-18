---
title: 檢視 Dll 和可執行檔
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 400961eaa14b87d70a685a87be5df48ac92c8281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906138"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>在 [模組] 視窗中檢視的 Dll 和可執行檔 (C#， C++，Visual Basic 中， F#)

Visual Studio 偵錯時，**模組** 視窗列出和顯示的 Dll 和可執行檔的相關資訊 (*.exe*檔案) 應用程式使用。

> [!NOTE]
> [模組] 視窗不能用於 SQL 或指令碼偵錯。

## <a name="use-the-modules-window"></a>使用 [模組] 視窗

若要偵錯時，請開啟 [模組] 視窗中，選取**偵錯** > **Windows** > **模組**(或按**Ctrl + Alt + U**).

根據預設，[模組] 視窗會依載入順序來排序模組。 若要排序視窗中的任何資料行，請選取頂端的資料行的標頭。

## <a name="load-symbols"></a>載入符號

**符號狀態**中的資料行**模組**視窗會顯示哪些模組已經載入偵錯符號。 如果狀態是 **略過載入符號**，**找不到或無法開啟 PDB 檔案**，或**透過包含/排除設定已停用載入**，您可以手動載入符號。 如需有關載入和使用符號的詳細資訊，請參閱 <<c0> [ 指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

**手動載入符號：**

1. 在 **模組**視窗中，以滑鼠右鍵按一下未載入符號的模組。

   - 選取 **符號載入資訊**之原因的相關詳細資料的未載入符號。

   - 選取 **載入符號**手動載入符號。

1. 如果未載入符號，請選取**符號設定**來開啟**選項** 對話方塊中，並指定或變更正在載入位置的符號。

   您可以從公用 Microsoft 符號伺服器或其他伺服器下載符號，或在您的電腦上，從資料夾載入符號。 如需詳細資訊，請參閱 <<c0> [ 指定符號位置和載入行為](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)。

**若要變更符號載入行為的設定：**

1. 在 [模組] 視窗中，以滑鼠右鍵按一下任一模組。

1. 選取 **符號設定**。

1. 選取 **載入所有符號**，或選取要包含或排除的模組。

1. 選取 [確定]。 變更將會在下一個偵錯工作階段中生效。

**若要變更符號載入特定模組的行為：**

1. 在 [模組] 視窗中，以滑鼠右鍵按一下模組。

1. 以滑鼠右鍵按一下功能表中，請選取或取消選取**永遠負載自動**。 變更將會在下一個偵錯工作階段中生效。

## <a name="see-also"></a>另請參閱
- [Breaking execution](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100)) (中斷執行)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)