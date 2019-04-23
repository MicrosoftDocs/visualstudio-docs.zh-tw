---
title: HOW TO：使用模組視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f332ef1a52ae49e51025614745fc1b5c4a44e07
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078280"
---
# <a name="how-to-use-the-modules-window"></a>HOW TO：使用模組視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
>  這個功能不能用於 SQL 或指令碼偵錯。  
  
 **模組**視窗會列出 Dll 和 EXE，供您的程式，並顯示每個的相關資訊。  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>若要在中斷模式或執行模式顯示模組視窗  
  
- 在 [**偵錯**] 功能表中，選擇**Windows**，然後按一下**模組**。  
  
     根據預設，[模組] 視窗會依載入順序來排序模組。 但您也可以選擇依任何資料行來排序。  
  
### <a name="to-sort-by-any-column"></a>若要依任何欄位排序  
  
- 請按一下欄位頂端的按鈕。  
  
     您可以載入符號或指定的符號路徑**模組**使用捷徑功能表的視窗。  
  
## <a name="loading-symbols"></a>載入符號  
 在 [**模組**] 視窗中，您可以看到哪些模組已經載入偵錯符號。 這項資訊會出現在**符號狀態**資料行。 如果這個狀態顯示**略過 loadingCannot 尋找或開啟 PDB 檔案**，或**透過包含/排除設定已停用載入**，您可以直接從 Microsoft 公用符號下載符號偵錯工具伺服器或從您的電腦上的符號目錄載入符號。 如需詳細資訊，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>若要手動載入符號  
  
1. 在 [**模組**] 視窗中，以滑鼠右鍵按一下未載入符號有的模組。  
  
2. 指向**載入符號來源**，然後按一下**Microsoft 符號伺服器**或是**符號路徑**。  
  
#### <a name="to-change-symbol-load-settings"></a>若要變更符號載入設定  
  
1. 在 [模組] 視窗中，以滑鼠右鍵按一下任一模組。  
  
2. 按一下 **符號設定**。  
  
     您現在可以變更符號載入設定，，如中所述[指定符號位置和載入行為](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)。 在重新啟動偵錯工作階段之前，變更不會生效。  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>若要變更特定模組的符號載入行為  
  
1. 在 [模組] 視窗中，以滑鼠右鍵按一下模組。  
  
2. 指向**自動符號載入設定**，然後按一下**永遠手動載入**或是**預設**。 在重新啟動偵錯工作階段之前，變更不會生效。  
  
## <a name="see-also"></a>另請參閱  
 [中斷執行](http://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
