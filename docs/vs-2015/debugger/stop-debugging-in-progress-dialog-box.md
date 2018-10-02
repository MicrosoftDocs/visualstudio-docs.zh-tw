---
title: 停止 [進度] 對話方塊中的偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e96e76f809f6c2f8f02267fe080e9e6742af4587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488108"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>停止進行中的偵錯對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[停止偵錯在進度對話方塊](https://docs.microsoft.com/visualstudio/debugger/stop-debugging-in-progress-dialog-box)。  
  
如果偵錯工具嘗試停止偵錯工作階段，但是工作階段需要一些時間才會停止，這個對話方塊就會出現。 停止偵錯工作階段通常很快就能完成，所以不會出現這個對話方塊。 不過，有時可能需要多花一些時間才能從所有正在偵錯的處理序中斷連結。 如果停止工作階段需花費數秒 (或是發生中斷連結錯誤)，這個對話方塊就會出現。 如果經常發生這種情況，可能是因為內部問題，建議您連絡產品支援服務。  
  
 您可以等候處理序中斷連結而且這個對話方塊消失，或使用**立即停止**按鈕強制立即終止。  
  
 **立即停止**  
 按一下這個按鈕會立即結束偵錯工作階段。 使用**立即停止**會終止，而不是中斷連結正在進行偵錯的處理程序。 如果您正在偵錯系統處理序，終止具有這些處理程序**立即停止**可以有非預期且不想要的效果。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [中斷連結程式](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)



