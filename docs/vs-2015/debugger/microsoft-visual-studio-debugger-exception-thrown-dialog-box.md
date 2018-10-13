---
title: Microsoft Visual Studio 偵錯工具 （擲回的例外狀況） 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c3ce3a3362c657d4302ba919c866d4a32055423
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226159"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio 偵錯工具 (擲回例外狀況) 對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的程式發生了例外狀況。 這個對話方塊將報告擲回的例外狀況類型。 您的程式碼需要處理這個例外狀況。 您可以選擇下列選項處理例外狀況：  
  
 **Break**  
 允許執行中斷偵錯工具。 中斷之前沒有叫用例外狀況處理常式。 如果您從中斷處繼續，就會叫用例外狀況處理常式。  
  
 **Continue**  
 允許繼續執行，讓例外狀況處理常式有機會處理例外狀況。 這個選項不適用於某些例外狀況類型。 **繼續**可讓應用程式繼續執行。 在原生應用程式中，它會導致重新擲回例外狀況。 在 Managed 應用程式中，它會導致程式終止，或是由主控應用程式處理例外狀況。  
  
> [!NOTE]
>  在 Managed 程式碼中發生未處理的例外狀況之後無法繼續執行。 選擇**繼續**managed 程式碼中處理的例外狀況會造成停止偵錯之後。  
  
 **略過**  
 允許繼續執行，而不叫用例外狀況處理常式。 由於不會叫用例外狀況處理常式，因此這會進一步導致包含其他例外狀況和錯誤等後果。 這個選項不適用於某些例外狀況類型。  
  
## <a name="see-also"></a>另請參閱  
 [使用偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)   
 [例外狀況的最佳做法](http://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [例外狀況處理](http://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)



