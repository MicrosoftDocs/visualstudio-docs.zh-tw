---
title: 可執行檔（用於偵測會話）對話方塊 |Microsoft Docs
description: 若要 debug DLL，您必須指定可執行檔來呼叫 DLL。 瞭解未指定可執行檔時所顯示的對話方塊。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870827"
---
# <a name="executable-for-debugging-session-dialog-box"></a>偵錯工作階段的可執行檔對話方塊

當您嘗試對未指定任何可執行檔的 DLL 進行偵錯時，就會出現這個對話方塊。 Visual Studio 無法直接啟動 DLL。 相反地，Visual Studio 會啟動指定的可執行檔。 您可以在可執行檔呼叫 DLL 時進行調試。

 **可執行檔名稱** 輸入可執行檔的路徑名稱，此可執行檔會呼叫您正在進行偵錯工具的 DLL。

 **只能 (ATL Server 存取專案的 URL)** 如果您正在進行 ATL Server DLL 的偵錯工具，請輸入可以找到專案的 URL。

 輸入之後，這些設定會儲存在專案屬性頁面中，因此您不需要再次輸入這些設定，即可進行後續的偵錯工具。 如果您需要變更設定，請開啟 [屬性頁] 並變更這些值。 如需有關為偵錯工具會話指定可執行檔的詳細資訊，請參閱 [偵錯工具 dll](../debugger/how-to-debug-from-a-dll-project.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)