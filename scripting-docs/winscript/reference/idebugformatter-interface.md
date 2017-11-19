---
title: "IDebugFormatter 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97f95aa1ecb91f6caca187939a79a6f09cd2108f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugformatter-interface"></a>IDebugFormatter 介面
允許的語言或 IDE 來自訂 VARIANT 值或 VARTYPE 類型與字串之間的轉換。  
  
 除了繼承自`IUnknown`、`IDebugFormatter`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|傳回表示指定的變數值的字串。|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|傳回包含指定的字串的 VARIANT。|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|傳回表示指定的 VARTYPE 值的字串。|