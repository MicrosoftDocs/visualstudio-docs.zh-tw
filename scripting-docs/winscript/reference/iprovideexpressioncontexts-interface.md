---
title: IProvideExpressionContexts Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410055"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts 介面
提供方法來列舉特定元件已知的運算式內容。 指令碼引擎通常會實作這個介面。  
  
 處理序偵錯管理員會使用此介面來尋找與指定的執行緒相關聯的所有全域運算式內容。  
  
> [!NOTE]
> 這個介面會從感興趣的執行緒內呼叫。 它是由實作者找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IProvideExpressionContexts`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|傳回這個元件的已知的運算式內容的列舉值。|