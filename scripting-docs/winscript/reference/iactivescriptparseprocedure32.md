---
title: IActiveScriptParseProcedure32 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144385"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
如果 Windows 腳本引擎允許將程式的原始程式碼文字加入至腳本，它就會執行 `IActiveScriptParseProcedure32` 介面。 對於沒有獨立撰寫環境的已解讀指令碼語言（例如 VBScript），這會提供替代機制 (`IActiveScriptParse32` 或 `IPersist` * ) ，將腳本程式新增至命名空間。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|說明|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|剖析指定的程式碼程式，並將程式新增至命名空間。|  
  
## <a name="see-also"></a>請參閱  
 [動態指令碼介面](../../winscript/reference/active-script-interfaces.md)