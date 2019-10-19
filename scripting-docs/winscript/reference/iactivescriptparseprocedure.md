---
title: IActiveScriptParseProcedure |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561665"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
如果 Windows 腳本引擎允許將程式的原始程式碼文字加入至腳本，它就會執行 `IActiveScriptParseProcedure` 介面。 對於沒有獨立撰寫環境的解讀式指令碼語言（例如 VBScript），這會提供替代機制（不是 `IActiveScriptParse` 或 `IPersist` *）來將腳本程式新增至命名空間。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|||  
|-|-|  
|方法|描述|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|剖析指定的程式碼程式，並將程式新增至命名空間。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)