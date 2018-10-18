---
title: 如何： 偵錯 ASP.NET 例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08e382ed9d97aa659012934d3edef45151e10ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178525"
---
# <a name="how-to-debug-aspnet-exceptions"></a>如何：偵錯 ASP.NET 例外狀況
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

偵錯例外狀況是很重要的一部分，開發強固的[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]應用程式。 如何偵錯例外狀況的一般資訊位於[偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 若要偵錯未處理的[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]例外狀況，您必須確定偵錯工具停止它們。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 執行階段擁有最上層例外狀況處理常式。 因此，偵錯工具預設為絕不會在未處理的例外狀況中斷。 若要擲回例外狀況時，偵錯工具中斷，您必須選取**例外狀況時中斷： 擲回**設定在該特定例外狀況**例外狀況** 對話方塊。  
  
 如果您已啟用 Just My Code**例外狀況時中斷： 擲回**不會造成偵錯工具立即中斷，如果.NET Framework 方法或其他系統程式碼中擲回例外狀況。 而是直到偵錯工具叫用非系統程式碼後才會停止執行。 因此，您不需要在發生例外狀況時，逐步執行系統程式碼。  
  
 Just My Code 可讓您更有用的另一個選項：**例外狀況時中斷： user-unhandled**。 如果為例外狀況選擇這個設定，偵錯工具則會在使用者程式碼中斷執行 (但是只有在使用者程式碼並未攔截和處理例外狀況時)。 因為這個處理常式是在非使用者程式碼中，所以這個設定會取消最上層 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 例外狀況處理常式的效果。  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>若要使用 Just My Code 啟用 ASP.NET 例外狀況的偵錯  
  
1.  在 **偵錯**功能表上，按一下**例外狀況**。  
  
     **例外狀況** 對話方塊隨即出現。  
  
2.  在上**Common Language Runtime 例外狀況**列中選取**擲回**或是**user-unhandled**。  
  
     若要使用**user-unhandled**設定，請**Just My Code**必須啟用...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>若要使用 ASP.NET 例外狀況處理的最佳作法  
  
-   對於您可以預期會發生例外狀況並知道如何處理的程式碼，請將 `try … catch` 區塊置於此程式碼周圍。 例如，如果應用程式正在呼叫 XML Web Service 或直接在 SQL Server，該程式碼應該在**try...catch**封鎖，因為有許多可能會發生的例外狀況。



