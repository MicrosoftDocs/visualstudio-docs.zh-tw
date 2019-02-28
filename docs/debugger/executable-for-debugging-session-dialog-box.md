---
title: 可執行檔進行偵錯工作階段 對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682787"
---
# <a name="executable-for-debugging-session-dialog-box"></a>偵錯工作階段的可執行檔對話方塊

當您嘗試對未指定任何可執行檔的 DLL 進行偵錯時，就會出現這個對話方塊。 Visual Studio 無法直接啟動 DLL。 相反地，Visual Studio 會啟動指定的可執行檔。 呼叫可執行檔時，您可以偵錯 DLL。

 **可執行檔名稱**輸入呼叫您要偵錯 DLL 的可執行檔的路徑名稱。

 **專案可以是其中的 URL 存取 (僅限 ATL Server)** 如果您正在偵錯對 ATL 伺服器 DLL，請輸入 URL 可在其中找到專案。

 輸入之後，這些設定會儲存在專案屬性頁，因此您不需要再次輸入後續的偵錯工作階段。 如果您需要變更設定，請開啟 [屬性頁] 並變更這些值。 如需為偵錯工作階段指定可執行檔的詳細資訊，請參閱[對 DLL 進行偵錯](../debugger/how-to-debug-from-a-dll-project.md)。

## <a name="see-also"></a>請參閱

- [Visual Studio 偵錯](../debugger/index.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)