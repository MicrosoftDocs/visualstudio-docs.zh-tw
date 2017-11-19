---
title: "IApplicationDebuggerUI 介面 |Microsoft 文件"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI 介面
藉由偵錯工具整合式的開發環境 (IDE) (除了`IApplicationDebugger`) 若要讓外部元件更充分掌控偵錯工具的使用者介面 (UI)。  
  
 除了繼承自`IUnknown`、`IApplicationDebuggerUI`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|將包含偵錯工具中的第一個指定的偵錯文件視窗顯示使用者介面。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|包含偵錯工具使用者介面中最上層的給定文件內容的視窗，且捲動視窗至內容。|