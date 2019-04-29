---
title: IDebugSessionProvider 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979044"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider 介面
偵錯工具來啟用主機和語言的 IDE 所提供的主要介面啟動偵錯。 它會建立執行中應用程式的偵錯工作階段。 機器偵錯管理員會實作這個介面。  
  
 除了繼承自方法`IUnknown`，則`IDebugSessionProvider`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|初始化具有指定的應用程式的偵錯工作階段。|