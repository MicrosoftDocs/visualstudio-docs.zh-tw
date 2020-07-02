---
title: IActiveScriptParse32 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835312"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
如果 Windows 腳本引擎允許將原始文字程式碼程式碼片段加入至腳本，或允許在執行時間評估運算式文字，則會執行 `IActiveScriptParse32` 介面。 對於沒有獨立撰寫環境的解讀式指令碼語言（例如 VBScript），這會提供替代機制（而不是 `IPersist*` ），以取得腳本引擎中的腳本，並將腳本片段附加至各種物件事件。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|將程式碼程式碼片段加入至腳本。|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|初始化腳本引擎。|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|剖析指定的程式碼程式碼片段、將宣告新增至命名空間，並適當地評估程式碼。|