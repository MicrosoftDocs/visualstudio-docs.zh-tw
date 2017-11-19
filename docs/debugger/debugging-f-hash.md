---
title: "偵錯 F # |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51eaed204db7b50e75a18dfac104a00546770abc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-f"></a>偵錯 F#
除了下列幾點差異，偵錯 F# 的方式與偵錯任何 Managed 語言非常類似：  
  
-   **自動變數**視窗不會顯示 F # 變數。  
  
-   F# 不支援 [編輯後繼續]。 在偵錯工作階段期間編輯 F# 程式碼是可行的作法，但應該避免。 因為偵錯工作階段期間不會套用程式碼變更，所以在偵錯期間編輯 F# 程式碼會導致原始程式碼與正在偵錯的程式碼變成不相符。  
  
-   偵錯工具無法辨識 F# 運算式。 若要於 F# 偵錯期間，在偵錯工具視窗或對話方塊中輸入運算式，您必須將運算式轉譯成 C# 語法。 當您將 F# 運算式轉譯成 C# 時，請切記 C# 使用 == 做為相等運算子，而 F# 則使用單一的 =。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
