---
title: Microsoft Visual Studio 偵錯工具 （擲回的例外狀況） 對話方塊 |Microsoft Docs
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1111bc7f3fbb0f515bfeb5247f70925c1ab304d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681279"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊
您的程式發生了例外狀況。 這個對話方塊將報告擲回的例外狀況類型。 您的程式碼需要處理這個例外狀況。 您可以選擇下列選項處理例外狀況：

 **中斷**允許執行中斷偵錯工具。 中斷之前沒有叫用例外狀況處理常式。 如果您從中斷處繼續，就會叫用例外狀況處理常式。

 **繼續**允許繼續執行，讓例外狀況處理常式有機會處理例外狀況。 這個選項不適用於某些例外狀況類型。 [繼續] 可讓應用程式繼續執行。 在原生應用程式中，它會導致重新擲回例外狀況。 在 Managed 應用程式中，它會導致程式終止，或是由主控應用程式處理例外狀況。

> [!NOTE]
>  在 Managed 程式碼中發生未處理的例外狀況之後無法繼續執行。 在受控程式碼中發生未處理的例外狀況之後選擇 [繼續]，將會導致偵錯停止。

 **忽略**可讓您繼續，而不叫用例外狀況處理常式的執行。 由於不會叫用例外狀況處理常式，因此這會進一步導致包含其他例外狀況和錯誤等後果。 這個選項不適用於某些例外狀況類型。

## <a name="see-also"></a>請參閱
- [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)
- [例外狀況的最佳做法](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [例外狀況處理](/cpp/windows/exception-handling-cpp-component-extensions)