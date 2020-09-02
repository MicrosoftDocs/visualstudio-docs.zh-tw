---
title: 停止進行中的調試對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4fc4b72987be726ab06aeb92a0e3eec2a338949e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684953"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>停止進行中的偵錯對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果偵錯工具嘗試停止偵錯工作階段，但是工作階段需要一些時間才會停止，這個對話方塊就會出現。 停止偵錯工作階段通常很快就能完成，所以不會出現這個對話方塊。 不過，有時可能需要多花一些時間才能從所有正在偵錯的處理序中斷連結。 如果停止工作階段需花費數秒 (或是發生中斷連結錯誤)，這個對話方塊就會出現。 如果經常發生這種情況，可能是因為內部問題，建議您連絡產品支援服務。  
  
 您可以等候處理序中斷連結和此對話方塊消失，也可使用 [立即停止]**** 按鈕強制立即終止。  
  
 [立即停止]****  
 按一下這個按鈕會立即結束偵錯工作階段。 **現在使用 Stop**會終止，而不是卸離正在進行調試的進程。 如果您正在偵錯系統處理序，使用 [立即停止]**** 終止這些處理序可能會產生非預期且不想要的結果。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [卸離程式](https://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
