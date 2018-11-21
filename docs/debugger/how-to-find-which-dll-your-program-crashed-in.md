---
title: 如何： 尋找程式損毀的所在的 DLL |Microsoft Docs
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
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257093"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>如何： 尋找程式損毀的所在的 DLL (C#，c + +、 Visual Basic 中， F#)
  
 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到程式以外的 DLL 中的損毀，您可以識別位置使用**模組**視窗。  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處  
  
1.  記下發生毀損的位址。

    如果位址不會顯示錯誤訊息，您可能需要使用替代方法來找出的 DLL。 如果您懷疑系統 DLL，您可以[載入符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)從偵錯時，才會進行 Microsoft 符號伺服器。 否則，您可能需要[建立傾印檔案](../debugger/using-dump-files.md)與堆積資訊改為。 各種[工具](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)可用於建立傾印檔案。
  
2.  在上**偵錯**功能表上，選擇**Windows**，然後按一下**模組**。  
  
3.  在 [**模組**] 視窗中，尋找**地址**資料行。 您可能需要使用捲軸才能看到它。  
  
4.  按一下 **地址**以便依位址排序 Dll 的資料行頂端的按鈕。  
  
5.  瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。  
  
6.  看看**名稱**並**路徑**若要查看的 DLL 名稱和路徑的資料行。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)   
 [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)