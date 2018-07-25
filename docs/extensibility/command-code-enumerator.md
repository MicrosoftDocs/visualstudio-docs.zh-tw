---
title: 命令碼列舉程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67c133339f47a3f15822e4ff79587f9a09253a66
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231970"
---
# <a name="command-code-enumerator"></a>命令碼列舉程式
這個列舉值使用中的選項[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)並[SccPopulateList](../extensibility/sccpopulatelist-function.md)表示指定之選項的命令。  
  
## <a name="syntax"></a>語法  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## <a name="members"></a>成員  
 SCC_COMMAND_GET  
 對應至[SccGet](../extensibility/sccget-function.md)。  
  
 SCC_COMMAND_CHECKOUT  
 對應至[SccCheckout](../extensibility/scccheckout-function.md)。  
  
 SCC_COMMAND_CHECKIN  
 對應至[SccCheckin](../extensibility/scccheckin-function.md)。  
  
 SCC_COMMAND_UNCHECKOUT  
 對應至[SccUncheckout](../extensibility/sccuncheckout-function.md)。  
  
 SCC_COMMAND_ADD  
 對應至[SccAdd](../extensibility/sccadd-function.md)。  
  
 SCC_COMMAND_REMOVE  
 對應至[SccRemove](../extensibility/sccremove-function.md)。  
  
 SCC_COMMAND_DIFF  
 對應至[SccDiff](../extensibility/sccdiff-function.md)。  
  
 SCC_COMMAND_HISTORY  
 對應至[SccHistory](../extensibility/scchistory-function.md)。  
  
 SCC_COMMAND_RENAME  
 對應至[SccRename](../extensibility/sccrename-function.md)。  
  
 SCC_COMMAND_PROPERTIES  
 對應至[SccProperties](../extensibility/sccproperties-function.md)。  
  
 SCC_COMMAND_OPTIONS  
 對應至[SccSetOption](../extensibility/sccsetoption-function.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)