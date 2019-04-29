---
title: IApplicationDebuggerUI 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f138492e5b0a465bb0f101c15457ed1021ab3d5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991087"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI 介面
藉由將偵錯工具整合式的開發環境 (IDE) (除了`IApplicationDebugger`) 提供給外部元件進一步控制偵錯工具的使用者介面 (UI)。  
  
 除了繼承自方法`IUnknown`，則`IApplicationDebuggerUI`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|使用者介面將包含偵錯工具中的第一個指定的偵錯文件的視窗。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|會包含偵錯工具使用者介面中的第一個指定的文件內容的視窗，以及捲動視窗至內容。|