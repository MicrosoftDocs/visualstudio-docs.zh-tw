---
title: 無法變更值對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfe275411346e499312ba51c50a3a2ac3f4ed7d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161655"
---
# <a name="cannot-change-value-dialog-box"></a>無法變更值對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124; `The name` *name* `does not exist in the current context` &#124; *various other messages*  
  
 當您在偵錯工具視窗 ([自動變數]、[監看式] 或 [區域變數] 視窗) 或 [快速監看式] 對話方塊中嘗試將變數內容變更為無效值時，這個訊息方塊就會出現。 例如，如果您將整數變數的值設定成字元字串，這個訊息方塊就會出現。  
  
## <a name="solution"></a>方案  
 確認您輸入偵錯工具視窗或 [快速監看式] 對話方塊內的輸入內容，對於您嘗試設定的變數而言是有效的值。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)
