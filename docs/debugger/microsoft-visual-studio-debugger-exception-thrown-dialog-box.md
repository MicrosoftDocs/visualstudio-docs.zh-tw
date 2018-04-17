---
title: Microsoft Visual Studio 偵錯工具 （擲回的例外狀況） 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1020711c21fb7171a8f7f8b87296d300f53b78b1
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊
您的程式發生了例外狀況。 這個對話方塊將報告擲回的例外狀況類型。 您的程式碼需要處理這個例外狀況。 您可以選擇下列選項處理例外狀況：  
  
 **Break**  
 允許執行中斷偵錯工具。 中斷之前沒有叫用例外狀況處理常式。 如果您從中斷處繼續，就會叫用例外狀況處理常式。  
  
 **Continue**  
 允許繼續執行，讓例外狀況處理常式有機會處理例外狀況。 這個選項不適用於某些例外狀況類型。 **繼續**可讓應用程式繼續執行。 在原生應用程式中，它會導致重新擲回例外狀況。 在 Managed 應用程式中，它會導致程式終止，或是由主控應用程式處理例外狀況。  
  
> [!NOTE]
>  在 Managed 程式碼中發生未處理的例外狀況之後無法繼續執行。 選擇**繼續**managed 程式碼中處理的例外狀況會導致停止偵錯之後。  
  
 **略過**  
 允許繼續執行，而不叫用例外狀況處理常式。 由於不會叫用例外狀況處理常式，因此這會進一步導致包含其他例外狀況和錯誤等後果。 這個選項不適用於某些例外狀況類型。  
  
## <a name="see-also"></a>請參閱  
 [管理例外狀況偵錯工具](../debugger/managing-exceptions-with-the-debugger.md)   
 [例外狀況的最佳做法](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [例外狀況處理](/cpp/windows/exception-handling-cpp-component-extensions)