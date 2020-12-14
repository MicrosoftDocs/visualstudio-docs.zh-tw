---
title: Debug ASP.NET 例外狀況 |Microsoft Docs
Description: 瞭解如何設定，讓偵錯工具停止 ASP.NET 應用程式中未處理的例外狀況。 您可以確保中斷發生在非系統程式碼中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 945e289f3da55c8884f4ec2cd115c65dbe3be237
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398645"
---
# <a name="how-to-debug-aspnet-exceptions"></a>如何：偵錯 ASP.NET 例外狀況
在開發強固的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式時，針對例外狀況進行偵錯是很重要的部分。 如何 [使用偵錯工具管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況的一般資訊。

 若要對未處理的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況進行偵錯，則必須確定偵錯工具是否會因為這些例外狀況而停止。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 執行階段擁有最上層例外狀況處理常式。 因此，偵錯工具預設為絕不會在未處理的例外狀況中斷。 若要在擲回例外狀況時中斷偵錯工具，您必須在 [例外狀況] 對話方塊中，為該特定例外狀況選取 [例外狀況為下列時中斷: Thrown] 設定。

 如果您已啟用 Just My Code，請 **在例外狀況發生時中斷：** 擲回例外狀況時，如果在 .net 方法或其他系統程式碼中擲回例外狀況，則不會導致偵錯工具立即中斷。 而是直到偵錯工具叫用非系統程式碼後才會停止執行。 因此，您不需要在發生例外狀況時，逐步執行系統程式碼。

 Just My Code 提供另一個更有用的選項：[例外狀況為下列時中斷: User-unhandled]。 如果為例外狀況選擇這個設定，偵錯工具則會在使用者程式碼中斷執行 (但是只有在使用者程式碼並未攔截和處理例外狀況時)。 因為這個處理常式是在非使用者程式碼中，所以這個設定會取消最上層 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 例外狀況處理常式的效果。

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>若要使用 Just My Code 啟用 ASP.NET 例外狀況的偵錯

1. 在 [偵錯] 功能表上，按一下 [例外狀況]。

     [例外狀況] 對話方塊隨即出現。

2. 在 [Common Language Runtime 例外狀況] 資料列中，選取 [擲回] 或 [使用者未處理]。

     若要使用 [使用者未處理] 設定，則必須啟用 [Just My Code]。

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>若要使用 ASP.NET 例外狀況處理的最佳作法

- 對於您可以預期會發生例外狀況並知道如何處理的程式碼，請將 `try ... catch` 區塊置於此程式碼周圍。 例如，如果應用程式正在呼叫 XML Web 服務或直接呼叫 SQL Server 時，因為許多例外狀況可能會發生，所以這段程式碼應該位於 **try ... catch** 區塊中。

## <a name="see-also"></a>另請參閱
- [ASP.NET 應用程式的偵錯工具](../debugger/how-to-enable-debugging-for-aspnet-applications.md)