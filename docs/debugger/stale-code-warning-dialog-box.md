---
title: 過時的程式碼警告對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e212602b317127cfd14adcd246a23cdd92ed86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281789"
---
# <a name="stale-code-warning-dialog-box"></a>過時程式碼警告對話方塊
會出現此對話方塊後變更為原生程式碼**編輯後繼續**無法立即套用。 因此，現在目前堆疊框架中的某些機器碼已過期，也就是過時了。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用過時程式碼](/visualstudio/debugger/edit-and-continue-visual-cpp#bkmk_how_to_work_with_stale_code)。  
  
 **不要再顯示此對話方塊**  
 如果選取這個核取方塊，[編輯後繼續] 以後將直接套用程式碼變更，並且不再請求允許變更。 您可以開啟這個警告一次移至**選項** 對話方塊中，開啟**偵錯**資料夾，按一下**編輯後繼續**頁面，然後選取**警告出現過時的程式碼**。  
  
## <a name="see-also"></a>另請參閱  
 [支援的程式碼變更 （c + +）](../debugger/supported-code-changes-cpp.md)   
 [選項對話方塊、偵錯、編輯後繼續](/visualstudio/debugger/edit-and-continue)