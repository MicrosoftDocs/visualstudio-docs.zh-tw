---
title: "IDebugSessionProvider 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider 介面
偵錯工具若要啟用主機和語言的 IDE 所提供的主要介面起始偵錯。 它會建立執行的應用程式的偵錯工作階段。 這個介面是由電腦偵錯管理員實作的。  
  
 除了繼承自`IUnknown`、`IDebugSessionProvider`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|初始化具有指定的應用程式偵錯工作階段。|