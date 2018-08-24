---
title: POPLISTFUNC |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 600ad01047a977050c474c9af139e0d279fe8b5b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639623"
---
# <a name="poplistfunc"></a>POPLISTFUNC
此回呼會提供給[SccPopulateList](../extensibility/sccpopulatelist-function.md) ide 而且由原始檔控制外掛程式用來更新檔案或目錄的清單 (也提供給`SccPopulateList`函式)。  
  
 當使用者選擇**取得**命令在 IDE 中，IDE 會顯示清單方塊的使用者可以取得的所有檔案。 不幸的是，IDE 不知道使用者可能會收到; 的所有檔案的確切清單只有外掛程式都具有這份清單。 如果其他使用者將檔案新增至原始程式碼控制項專案中，這些檔案應該會出現在清單中，但在 IDE 不知道它們。 IDE 會建置它認為使用者可以取得檔案的清單。 向使用者顯示此清單之前，它會呼叫[SccPopulateList](../extensibility/sccpopulatelist-function.md) `,`讓原始檔控制外掛程式機會加入，並從清單中刪除檔案。  
  
## <a name="signature"></a>簽章  
 原始檔控制外掛程式會修改清單，藉由呼叫 IDE 實作函式具有下列原型：  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>參數  
 pvCallerData  
 `pvCallerData`參數傳遞至呼叫端 (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md)。 原始檔控制外掛程式應該假設任何有關此參數的內容。  
  
 fAddRemove  
 如果`TRUE`，`lpFileName`是應該加入的檔案清單的檔案。 如果`FALSE`，`lpFileName`是應該從檔案清單中刪除的檔案。  
  
 nStatus  
 狀態`lpFileName`(組成`SCC_STATUS`位元; 請參閱[檔案狀態碼](../extensibility/file-status-code-enumerator.md)如需詳細資訊)。  
  
 lpFileName  
 若要新增或從清單中刪除的檔案名稱的完整目錄路徑。  
  
## <a name="return-value"></a>傳回值  
  
|值|描述|  
|-----------|-----------------|  
|`TRUE`|此外掛程式可以繼續呼叫此函式。|  
|`FALSE`|在 IDE 端 （例如不足的記憶體的情況） 已有問題。 外掛程式應該停止的作業。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式想要加入或刪除的檔案清單中的每個檔案，它會呼叫此函式，並傳入`lpFileName`。 `fAddRemove`旗標會指出新的檔案新增至清單或刪除舊的檔案。 `nStatus`參數會提供檔案的狀態。 當外掛程式 SCC 完成新增及刪除檔案時，它會傳回[SccPopulateList](../extensibility/sccpopulatelist-function.md)呼叫。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST`功能位元是需要 Visual Studio。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)