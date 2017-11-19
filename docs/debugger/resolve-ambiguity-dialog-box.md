---
title: "解決語意模糊對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.Disambig
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
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0050ccdb3a4ccbd2d1d116239ad6fd6aba2032e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="resolve-ambiguity-dialog-box"></a>解決語意模糊對話方塊
當偵錯工具無法選擇要顯示的位置時，[`Resolve Ambiguity`] 對話方塊就會出現。 例如，如果您使用的是 C++ 範本，就可以從單一函式樣板建立多個函式。 如果偵錯工具停在樣板中的來源位置上，而且您選擇 [`Go To Disassembly`]，偵錯工具將擁有多個選項。 每個從樣板建立的函式都有自己的反組譯程式碼，而偵錯工具並不知道您想要檢視哪個程式碼。 [`Resolve Ambiguity`] 對話方塊可讓您從所有對應位置的清單中選取您要的位置。  
  
 `Choose the specific location`  
 列出對應至命令的所有位置。  
  
 `Address`  
 顯示每個函式的記憶體位址。  
  
 `Function`  
 顯示每個函式的名稱。  
  
 `Module`  
 顯示包含函式之目的碼的模組 (EXE 或 DLL)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)