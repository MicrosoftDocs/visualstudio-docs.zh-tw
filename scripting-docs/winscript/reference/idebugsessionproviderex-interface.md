---
title: "IDebugSessionProviderEx 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx 介面
提供 IDE，可啟用主控件和語言初始化偵錯的偵錯工具的主要介面。 它會建立執行的應用程式的偵錯工作階段。 這個介面是由電腦偵錯管理員實作的。  
  
 除了繼承自`IUnknown`、`IDebugSessionProviderEx`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|判斷是否與指定的應用程式可能只在階段偵錯。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|初始化具有指定的應用程式偵錯工作階段。|