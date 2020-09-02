---
title: 如何：使用模組視窗 |Microsoft Docs
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
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696132"
---
# <a name="how-to-use-the-modules-window"></a>如何：使用模組視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 這個功能不能用於 SQL 或指令碼偵錯。  
  
 [ **模組** ] 視窗會列出您的程式所使用的 DLL 和 EXE，並顯示每個 DLL 和 EXE 的相關資訊。  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>若要在中斷模式或執行模式顯示模組視窗  
  
- 在 [ **調試** ] 功能表上，選擇 [ **視窗**]，然後按一下 [ **模組**]。  
  
     根據預設，[模組]**** 視窗會依載入順序來排序模組。 但您也可以選擇依任何資料行來排序。  
  
### <a name="to-sort-by-any-column"></a>若要依任何欄位排序  
  
- 請按一下欄位頂端的按鈕。  
  
     您可以使用快捷方式功能表，從 [ **模組** ] 視窗載入符號或指定符號路徑。  
  
## <a name="loading-symbols"></a>載入符號  
 在 [ **模組** ] 視窗中，您可以看到哪些模組已載入調試符號。 這項資訊會出現在 [ **符號狀態** ] 資料行中。 如果狀態顯示 [已 **略過 loadingCannot 尋找或開啟 PDB**檔]，或 [ **包含/排除] 設定已停用**，您可以指示偵錯工具從 Microsoft 公用符號伺服器下載符號，或從電腦上的符號目錄載入符號。 如需詳細資訊，請參閱[指定符號 ( .pdb) 和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔  
  
#### <a name="to-load-symbols-manually"></a>若要手動載入符號  
  
1. 在 [ **模組** ] 視窗中，以滑鼠右鍵按一下尚未載入符號的模組。  
  
2. 指向 [ **載入符號來源** ]，然後按一下 [ **Microsoft 符號伺服器** ] 或 [ **符號路徑**]。  
  
#### <a name="to-change-symbol-load-settings"></a>若要變更符號載入設定  
  
1. 在 [模組]**** 視窗中，以滑鼠右鍵按一下任一模組。  
  
2. 按一下 [ **符號設定**]。  
  
     您現在可以變更符號載入設定，如 [指定符號位置和載入行為](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)中所述。 在重新啟動偵錯工作階段之前，變更不會生效。  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>若要變更特定模組的符號載入行為  
  
1. 在 [模組]**** 視窗中，以滑鼠右鍵按一下模組。  
  
2. 指向 [ **自動符號載入設定** ]，然後按一下 [ **一律手動載入** ] 或 [ **預設**]。 在重新啟動偵錯工作階段之前，變更不會生效。  
  
## <a name="see-also"></a>另請參閱  
 [中斷執行](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
