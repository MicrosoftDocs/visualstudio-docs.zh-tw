---
title: HOW TO：尋找程式損毀的所在的 DLL |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a9421af9e0caf085feb1afb27b53befe837668
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894043"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>HOW TO：尋找程式損毀的所在的 DLL (C#， C++，Visual Basic 中， F#)

 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到的損毀是由程式以外的 DLL 所致，您可以使用 [模組] 視窗來辨識其位置。

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處

1. 記下發生毀損的位址。

    如果位址不會顯示錯誤訊息，您可能需要使用替代方法來找出的 DLL。 如果您懷疑系統 DLL，您可以[載入符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)從偵錯時，才會進行 Microsoft 符號伺服器。 否則，您可能需要[建立傾印檔案](../debugger/using-dump-files.md)與堆積資訊改為。 各種[工具](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)可用於建立傾印檔案。

2. 在 [偵錯] 功能表上選擇 [Windows]，然後按一下 [模組]。

3. 在 [模組] 視窗中尋找出 [位址] 欄位。 您可能需要使用捲軸才能看到它。

4. 按一下 [位址] 按鈕 (在該欄位的最上方) 以便依位址排序 DLL。

5. 瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。

6. 檢視 [名稱] 和 [路徑] 欄位以查看此 DLL 名稱和路徑。

## <a name="see-also"></a>另請參閱
- [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)
- [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)