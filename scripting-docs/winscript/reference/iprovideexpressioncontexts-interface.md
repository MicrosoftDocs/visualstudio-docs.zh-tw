---
title: IProvideExpressionContexts 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728098"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts 介面
提供要列舉的特定元件的已知的運算式內容的方式。 指令碼引擎通常會實作這個介面。  
  
 處理序偵錯管理員會使用這個介面來尋找與給定的執行緒相關聯的所有全域運算式內容。  
  
> [!NOTE]
>  感興趣的執行緒中呼叫這個介面。 它是由實作者，找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="methods"></a>方法  
 除了繼承自`IUnknown`、`IProvideExpressionContexts`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|傳回這個元件的已知的運算式內容的列舉值。|