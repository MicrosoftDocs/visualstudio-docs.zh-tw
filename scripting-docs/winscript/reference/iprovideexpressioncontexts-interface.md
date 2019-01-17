---
title: IProvideExpressionContexts Interface | Microsoft Docs
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
ms.openlocfilehash: 91f4251fec57001ba6c7a4ea1804ec72371418bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345093"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts 介面
提供方法來列舉特定元件已知的運算式內容。 指令碼引擎通常會實作這個介面。  
  
 處理序偵錯管理員會使用此介面來尋找與指定的執行緒相關聯的所有全域運算式內容。  
  
> [!NOTE]
>  這個介面會從感興趣的執行緒內呼叫。 它是由實作者找出目前的執行緒，並傳回適當的列舉值。  
  
## <a name="methods"></a>方法  
 除了繼承自方法`IUnknown`，則`IProvideExpressionContexts`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|傳回這個元件的已知的運算式內容的列舉值。|