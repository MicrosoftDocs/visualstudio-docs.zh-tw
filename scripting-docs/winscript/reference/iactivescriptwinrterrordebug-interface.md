---
title: IActiveScriptWinRTErrorDebug 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e7728b4143231912227e5e55faa5eef01b7490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425792"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug 介面
藉由將 JavaScript 引擎，以提供從擴充的 Windows 執行階段錯誤資訊[BREAKREASON 列舉](../../winscript/reference/breakreason-enumeration.md)事件。 您可以執行以取得從 QueryInterface [IActiveScriptError](../../winscript/reference/iactivescripterror.md)物件。  
  
> [!IMPORTANT]
> 這個介面是由 PDM v11.0 和更新版本所實作。 可在 activdbg100.h 中找到。  
  
## <a name="methods"></a>方法  
 `IActiveScriptWinRTErrorDebug` 介面公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|如果有的話，會傳回 Windows 執行階段錯誤，功能 SID。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|傳回 Windows 執行階段會限制錯誤參考字串，如果有的話。|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|如果有的話，會傳回 Windows 執行階段會限制錯誤字串。|