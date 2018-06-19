---
title: IActiveScriptErrorDebug110 介面 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 152f12154acc59b88fc8b1c9a176ac87a5da847d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645758"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 介面
將功能加入[IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)。 這個介面是由 JavaScript 引擎所實作，用於判斷為何會發生 BREAKREASON_ERROR 事件。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IActiveScriptErrorDebug110` 介面公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|傳回已擲回之例外狀況的例外狀況類型。|