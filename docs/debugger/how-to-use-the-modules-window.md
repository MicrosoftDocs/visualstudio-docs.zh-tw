---
title: 查看 Dll 和可執行檔
description: 查看 Dll 和可執行檔 (.exe 檔案，) 您的應用程式在 Visual Studio 的偵錯工具期間，在 [模組] 視窗中使用這些檔案。
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385405"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>在 [模組] 視窗中查看 Dll 和可執行檔 (c #、c + +、Visual Basic、F # ) 

在 Visual Studio 的偵錯工具期間，[ **模組** ] 視窗會列出並顯示 dll 和可執行檔的相關資訊 (*.exe*) 您的應用程式所使用的檔案。

> [!NOTE]
> [模組] 視窗無法用於 SQL 或腳本的偵錯工具。

## <a name="use-the-modules-window"></a>使用 [模組] 視窗

若要在您進行調試時開啟 [模組] 視窗，請選取 [ **Debug**  >  **Windows**  >  **模組** (]，或按 **Ctrl + Alt + U**) 。

根據預設，[模組] 視窗會依載入順序來排序模組。 若要依任何視窗資料行排序，請選取資料行頂端的標頭。

## <a name="load-symbols"></a>載入符號

[**模組**] 視窗中的 [**符號狀態**] 欄會顯示已載入調試符號的模組。 如果已 **略過載入符號** 的狀態、找 **不到或無法開啟 PDB** 檔案，或 **包含/排除設定已停用載入**，您可以手動載入符號。 如需載入和使用符號的詳細資訊，請參閱 [指定符號 ( .pdb) 和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔。

**手動載入符號：**

1. 在 [ **模組** ] 視窗中，以滑鼠右鍵按一下尚未載入符號的模組。

   - 選取 **符號載入資訊** ，以取得為何未載入符號的詳細資料。

   - 選取 [ **載入符號** ] 以手動載入符號。

1. 如果未載入符號，請選取 [ **符號設定** ] 以開啟 [ **選項** ] 對話方塊，並指定或變更符號載入位置。

   您可以從公用 Microsoft 符號伺服器或其他伺服器下載符號，或從電腦上的資料夾載入符號。 如需詳細資訊，請參閱 [指定符號位置和載入行為](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)。

**若要變更符號載入行為設定：**

1. 在 [模組] 視窗中，以滑鼠右鍵按一下任一模組。

1. 選取 [ **符號設定**]。

1. 選取 [ **載入所有符號**]，或選取要包含或排除的模組。

1. 選取 [確定]。 變更會在下一個調試會話中生效。

**若要變更特定模組的符號載入行為：**

1. 在 [模組] 視窗中，以滑鼠右鍵按一下模組。

1. 在快顯功能表中，選取或取消選取 [ **一律自動載入**]。 變更會在下一個調試會話中生效。

## <a name="see-also"></a>另請參閱
- [中斷執行](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)
- [指定符號 ( .pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)