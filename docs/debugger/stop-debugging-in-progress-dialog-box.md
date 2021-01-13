---
title: 停止進行中的調試對話方塊 |Microsoft Docs
description: 探索 [停止進行中的偵錯工具] 對話方塊，這會在偵錯工具嘗試停止偵錯工具時出現，但停止會話需要一些時間。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c3ff46a8cd9b8e5a4ab80b0af1296348ca788d9
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150219"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>停止進行中的偵錯對話方塊
如果偵錯工具嘗試停止偵錯工作階段，但是工作階段需要一些時間才會停止，這個對話方塊就會出現。 停止偵錯工作階段通常很快就能完成，所以不會出現這個對話方塊。 不過，有時可能需要多花一些時間才能從所有正在偵錯的處理序中斷連結。 如果停止工作階段需花費數秒 (或是發生中斷連結錯誤)，這個對話方塊就會出現。 如果經常發生這種情況，可能是因為內部問題，建議您連絡產品支援服務。

 您可以等候處理序中斷連結和此對話方塊消失，也可使用 [立即停止] 按鈕強制立即終止。

 **立即停止** 按一下這個按鈕，立即結束調試會話。 **現在使用 Stop** 會終止，而不是卸離正在進行調試的進程。 如果您正在偵錯系統處理序，使用 [立即停止] 終止這些處理序可能會產生非預期且不想要的結果。

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [卸離程式](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))