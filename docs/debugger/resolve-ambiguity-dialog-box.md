---
title: 解決語意模糊對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d784766e3c90241be3759a7113c52e6d863fa47
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902657"
---
# <a name="resolve-ambiguity-dialog-box"></a>解決語意模糊對話方塊
當偵錯工具無法選擇要顯示的位置時，[`Resolve Ambiguity`] 對話方塊就會出現。 例如，如果您使用的是 C++ 範本，就可以從單一函式樣板建立多個函式。 如果偵錯工具停在樣板中的來源位置上，而且您選擇 [`Go To Disassembly`]，偵錯工具將擁有多個選項。 每個從樣板建立的函式都有自己的反組譯程式碼，而偵錯工具並不知道您想要檢視哪個程式碼。 [`Resolve Ambiguity`] 對話方塊可讓您從所有對應位置的清單中選取您要的位置。

 `Choose the specific location`列出對應至命令的所有位置。

 `Address`顯示每個函式的記憶體位址。

 `Function` 顯示每個函式的名稱。

 `Module`顯示包含函式目的碼的模組 (EXE 或 DLL)。

## <a name="see-also"></a>另請參閱
- [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)