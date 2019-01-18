---
title: IApplicationDebuggerUI 介面 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e3c5f9e4cabeb4fba31bb039a7cf673ca1759860
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348902"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI 介面
藉由將偵錯工具整合式的開發環境 (IDE) (除了`IApplicationDebugger`) 提供給外部元件進一步控制偵錯工具的使用者介面 (UI)。  
  
 除了繼承自方法`IUnknown`，則`IApplicationDebuggerUI`介面會公開下列方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|使用者介面將包含偵錯工具中的第一個指定的偵錯文件的視窗。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|會包含偵錯工具使用者介面中的第一個指定的文件內容的視窗，以及捲動視窗至內容。|