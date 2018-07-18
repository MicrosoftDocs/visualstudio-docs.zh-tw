---
title: 如何： 尋找所在的 DLL 程式損毀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 350cd8a78780eb8ddb2a197ed1e8920fda23bbf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474823"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>如何：尋找程式損毀時所在的 DLL
  
 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到損毀的 dll 程式以外，您可以識別位置使用**模組**視窗。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處  
  
1.  記下發生毀損的位址。

    如果位址不會顯示錯誤訊息中，您可能需要使用替代方法來找出的 DLL。 如果您懷疑系統 DLL，您可以[載入符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)從偵錯時，才會進行 Microsoft 符號伺服器。 否則，您可能需要[建立傾印檔案](../debugger/using-dump-files.md)與堆積資訊改為。 各種[工具](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)可用來建立傾印檔案。
  
2.  在**偵錯**功能表上，選擇**Windows**，然後按一下**模組**。  
  
3.  在**模組**視窗中，尋找**位址**資料行。 您可能需要使用捲軸才能看到它。  
  
4.  按一下**位址**以便依位址排序 Dll 的資料行頂端的按鈕。  
  
5.  瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。  
  
6.  查看**名稱**和**路徑**資料行，以查看此 DLL 名稱和路徑。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)