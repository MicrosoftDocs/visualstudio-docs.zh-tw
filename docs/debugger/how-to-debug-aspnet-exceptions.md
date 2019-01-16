---
title: HOW TO：偵錯 ASP.NET 例外狀況 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 002f100f11bd88e31b94283e7efe5e25299448bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944294"
---
# <a name="how-to-debug-aspnet-exceptions"></a>HOW TO：針對 ASP.NET 例外狀況進行偵錯
在開發強固的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式時，針對例外狀況進行偵錯是很重要的部分。 如何偵錯例外狀況的一般資訊位於[偵錯工具管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。  
  
 若要對未處理的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況進行偵錯，則必須確定偵錯工具是否會因為這些例外狀況而停止。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 執行階段擁有最上層例外狀況處理常式。 因此，偵錯工具預設為絕不會在未處理的例外狀況中斷。 若要擲回例外狀況時，偵錯工具中斷，您必須選取**例外狀況時中斷：擲回**設定為在該特定例外狀況**例外狀況** 對話方塊。  
  
 如果您已啟用 Just My Code，**例外狀況時中斷：擲回**不會造成偵錯工具立即中斷，如果.NET Framework 方法或其他系統程式碼中擲回例外狀況。 而是直到偵錯工具叫用非系統程式碼後才會停止執行。 因此，您不需要在發生例外狀況時，逐步執行系統程式碼。  
  
 Just My Code 會提供更有用的另一個選項：**例外狀況時中斷：使用者未處理**。 如果為例外狀況選擇這個設定，偵錯工具則會在使用者程式碼中斷執行 (但是只有在使用者程式碼並未攔截和處理例外狀況時)。 因為這個處理常式是在非使用者程式碼中，所以這個設定會取消最上層 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況處理常式的效果。  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>若要使用 Just My Code 啟用 ASP.NET 例外狀況的偵錯  
  
1.  在 [偵錯] 功能表上，按一下 [例外狀況]。  
  
     [例外狀況] 對話方塊隨即出現。  
  
2.  在 [Common Language Runtime 例外狀況] 資料列中，選取 [擲回] 或 [使用者未處理]。  
  
     若要使用 [使用者未處理] 設定，則必須啟用 [Just My Code]。  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>若要使用 ASP.NET 例外狀況處理的最佳作法  
  
-   對於您可以預期會發生例外狀況並知道如何處理的程式碼，請將 `try ... catch` 區塊置於此程式碼周圍。 例如，如果應用程式正在呼叫 XML Web 服務或直接呼叫 SQL Server 時，因為許多例外狀況可能會發生，所以這段程式碼應該位於 **try ... catch** 區塊中。

## <a name="see-also"></a>請參閱
[針對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)