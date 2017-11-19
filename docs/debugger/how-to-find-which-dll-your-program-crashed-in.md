---
title: "如何： 尋找所在的 DLL 程式損毀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6232f86e9e9f5d59e9e109d08b75120cc90902c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>如何：尋找程式損毀時所在的 DLL
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到損毀的 dll 程式以外，您可以識別位置使用**模組**視窗。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處  
  
1.  記下發生毀損的位址。  
  
2.  在**偵錯**功能表上，選擇**Windows**，然後按一下**模組**。  
  
3.  在**模組**視窗中，尋找**位址**資料行。 您可能需要使用捲軸才能看到它。  
  
4.  按一下**位址**以便依位址排序 Dll 的資料行頂端的按鈕。  
  
5.  瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。  
  
6.  查看**名稱**和**路徑**資料行，以查看此 DLL 名稱和路徑。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)