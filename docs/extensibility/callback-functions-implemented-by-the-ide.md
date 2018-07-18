---
title: IDE 所實作的回呼函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109684"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE 所實作的回呼函式
若要與整合整合式的開發環境 (IDE)，以作為無縫越好，並提供整合的經驗，原始檔控制外掛程式可以使用 IDE 所實作的回呼函式。 外掛程式可以呼叫這些函式在適當時將資訊傳遞至 IDE; 原始檔控制作業的時間IDE 可以做為內嵌的項目在其原生的 UI 中顯示這項資訊。 使用者擁有較低分散的體驗，在此案例中比如果外掛程式採用自己的 UI。  
  
 必要的標頭檔是 scc.h。 預設位置是 \Program Files\VSIP 8.0\EnvSDK\common\inc\\。 此外也會在 \Program Files\VSIP 8.0\MSSCCI 有原始檔控制外掛程式範例的 VSIP 資料夾中\\。  
  
## <a name="in-this-section"></a>本節內容  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 描述回呼函式，以供[SccOpenProject](../extensibility/sccopenproject-function.md)顯示從原始檔控制外掛程式透過 IDE 的訊息。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 描述回呼函式，以供[SccPopulateList](../extensibility/sccpopulatelist-function.md)當 IDE 未完整存取權僅適用於原始檔控制外掛程式，例如版本控制下的檔案的完整清單的資訊。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 描述回呼函式，以供[SccQueryChanges](../extensibility/sccquerychanges-function.md)作業。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 描述回呼函式，以供[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)作業。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 描述設定呼叫的回呼函式[SccSetOption](../extensibility/sccsetoption-function.md) ，可讓原始檔控制外掛程式，以便在通訊回到 IDE 的名稱變更。  
  
## <a name="related-sections"></a>相關章節  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 開啟專案。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 會檢查其目前狀態的檔案清單。 此外，使用`pfnPopulate`函式的檔案不相符的準則時，通知呼叫端`nCommand`。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 會檢查目錄和檔案的專案或在原始檔控制的專案中的清單。 找到的每個目錄和檔案名稱傳遞至回呼函式。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 會檢查檔案的清單所做的變更名稱。 每個檔案名稱傳遞至回呼函式，以及其變更狀態。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 設定各種不同的選項。 每個選項開頭`SCC_OPT_xxx`而且有它自己組定義的值。  
  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)  
 描述原始檔控制外掛程式 SDK 的參考章節的內容。