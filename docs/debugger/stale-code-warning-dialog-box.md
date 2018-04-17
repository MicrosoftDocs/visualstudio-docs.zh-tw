---
title: 過時程式碼警告對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 77fbbd558e424103b8d6ecc69e3724c9011365c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="stale-code-warning-dialog-box"></a>過時程式碼警告對話方塊
會出現此對話方塊後變更原生程式碼的**編輯後繼續**無法立即套用。 因此，現在目前堆疊框架中的某些機器碼已過期，也就是過時了。 如需詳細資訊，請參閱[How to： 使用過時程式碼](http://msdn.microsoft.com/en-us/c7536e95-66a6-44a0-995d-3fe5035250b4)。  
  
 **不要再顯示此對話方塊**  
 如果選取這個核取方塊，[編輯後繼續] 以後將直接套用程式碼變更，並且不再請求允許變更。 您可以開啟這個警告在上一次，請前往**選項**對話方塊中，開啟**偵錯**資料夾中，按一下**編輯後繼續**頁面，然後選取**警告出現過時的程式碼**。  
  
## <a name="see-also"></a>請參閱  
 [支援的程式碼變更 （c + +）](../debugger/supported-code-changes-cpp.md)   
 [編輯後繼續、 偵錯、 選項對話方塊](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)