---
title: 過時程式碼警告對話方塊 |Microsoft Docs
description: 閱讀 [過時程式碼警告] 對話方塊，當您對 [編輯後繼續] 無法立即套用的機器碼進行變更時，就會出現此對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2666b3b57c8f84c81e181355f096674543445
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150323"
---
# <a name="stale-code-warning-dialog-box"></a>過時程式碼警告對話方塊

當您對 [編輯後繼續] 無法立即套用的機器碼進行變更時，這個對話方塊就會出現。 因此，現在目前堆疊框架中的某些機器碼已過期，也就是過時了。 如需詳細資訊，請參閱[編輯後繼續 (C++)](edit-and-continue-visual-cpp.md)。

**不要再顯示此對話方塊**

如果選取這個核取方塊，[編輯後繼續] 以後將直接套用程式碼變更，並且不再請求允許變更。 您可以在 [選項] 對話方塊中開啟 [偵錯] 資料夾，按一下 [編輯後繼續] 頁面，然後選取 [警告出現過時的程式碼]，即可重新開啟這個警告。

## <a name="see-also"></a>另請參閱

- [支援的程式碼變更 (C++)](supported-code-changes-cpp.md)
- [選項對話方塊、偵錯、編輯後繼續](edit-and-continue.md)