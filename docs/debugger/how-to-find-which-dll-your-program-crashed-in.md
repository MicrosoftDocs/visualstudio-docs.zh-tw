---
title: 找出程式損毀的 DLL |Microsoft Docs
description: 您可以使用 [模組] 視窗，識別當應用程式損毀時，所使用的外部 DLL。 您可以針對系統 DLL 或他人的程式碼進行此作業。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6eacc8865b3f531df8651ad77d99b319278e6cd1
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903386"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>如何：找出您的程式在 (c #、c + +、Visual Basic、F # ) 中損毀的 DLL

 如果您的應用程式在呼叫系統 DLL 或其他程式碼時損毀，您就必須找出發生損毀時作用中的 DLL。 如果您遇到的損毀是由程式以外的 DLL 所致，您可以使用 [模組] 視窗來辨識其位置。

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>若要使用模組視窗來尋找毀損之處

1. 記下發生毀損的位址。

    如果錯誤訊息中沒有顯示位址，您可能需要使用替代方法來識別 DLL。 如果您懷疑系統 DLL，您可以在調試時從 Microsoft 符號伺服器 [載入符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 。 否則，您可能需要改為 [建立](../debugger/using-dump-files.md) 包含堆積資訊的傾印檔案。 您可以使用各種 [工具](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) 來建立傾印檔案。

2. 在 [偵錯] 功能表上選擇 [Windows]，然後按一下 [模組]。

3. 在 [模組] 視窗中尋找出 [位址] 欄位。 您可能需要使用捲軸才能看到它。

4. 按一下 [位址] 按鈕 (在該欄位的最上方) 以便依位址排序 DLL。

5. 瀏覽此排序清單，找出位址範圍包含毀損位置的 DLL。

6. 檢視 [名稱] 和 [路徑] 欄位以查看此 DLL 名稱和路徑。

## <a name="see-also"></a>另請參閱
- [偵錯 DLL 專案](../debugger/debugging-dll-projects.md)
- [如何：使用模組視窗](../debugger/how-to-use-the-modules-window.md)