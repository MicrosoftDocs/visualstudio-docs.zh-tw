---
title: IActiveScriptErrorDebug110 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 72f545f5a48fc7b8aa3f9250b13a62ba659e94bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436061"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 介面
將功能加入至[IActiveScriptDebug 介面](../../winscript/reference/iactivescriptdebug-interface.md)。 這個介面是由 JavaScript 引擎所實作，用於判斷為何會發生 BREAKREASON_ERROR 事件。  
  
> [!IMPORTANT]
> 這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IActiveScriptErrorDebug110` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|傳回已擲回之例外狀況的例外狀況類型。|