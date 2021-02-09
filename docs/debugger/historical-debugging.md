---
title: 歷程記錄調試 |Microsoft Docs
description: 藉由檢查應用程式的狀態，讓應用程式在執行時繼續進行疑難排解。 Intellitrace 會收集這項功能的資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4a6bf07cc7905fc48bcc82c8b38fa5b6f6e7cfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904408"
---
# <a name="historical-debugging-c-visual-basic-c"></a> (c #、Visual Basic、c + +) 的歷程記錄調試

歷程偵錯是取決於 IntelliTrace 所收集資訊的偵錯模式。 它可讓您向後和向前逐步執行您的應用程式，並檢查其狀態。

 您可以在 Visual Studio Enterprise 版本 (而非 Professional 或 Community 版本) 中使用 IntelliTrace。

## <a name="why-use-historical-debugging"></a>為何使用歷程偵錯？

 設定中斷點來找出 Bug 可能相當容易出錯。 您可以在接近程式碼中懷疑為 Bug 所在的位置設定中斷點，然後在偵錯工具中執行應用程式，並希望您的中斷點找到錯誤位置，以及執行中斷可能會顯示 Bug 來源的位置。 否則，您必須嘗試在程式碼的某一處設定中斷點，然後重新執行偵錯工具，以重複執行測試步驟，直到找出問題。

 ![設定中斷點](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 您可以使用 IntelliTrace 和歷程偵錯來漫遊應用程式，並檢查其狀態 (呼叫堆疊和區域變數)，而不需要設定中斷點、重新啟動偵錯，以及重複測試步驟。 這可以節省許多時間，特別是當 Bug 位於測試案例的較深處而需要花很長的時間執行時。

## <a name="how-do-i-start-using-historical-debugging"></a>如何開始使用歷程偵錯？

預設會開啟 IntelliTrace。 您只需決定要對您感興趣的事件和函數呼叫，以及是否要查看完整應用程式狀態的快照集。 如需定義您想要尋找之項目的詳細資訊，請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。 功能支援會因語言和應用程式類型而異。

- 若要使用歷程記錄偵錯工具來查看快照集，請參閱 [使用 IntelliTrace 檢查先前的應用程式狀態](../debugger/view-historical-application-state.md)
- 若要瞭解如何檢查變數和流覽程式碼，請參閱 [使用歷程記錄來檢查應用程式](../debugger/historical-debugging-inspect-app.md)
- 若要深入了解使用 IntelliTrace 事件偵錯，請參閱[逐步解說： 使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。