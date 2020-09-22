---
title: POPLISTFUNC |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2020
ms.locfileid: "90839035"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此回呼會由 IDE 提供給 [SccPopulateList](../extensibility/sccpopulatelist-function.md) ，並且由原始檔控制外掛程式用來更新檔案或目錄的清單， (也提供給 `SccPopulateList` 函數) 。  
  
 當使用者在 IDE 中選擇 **Get** 命令時，ide 會顯示使用者可取得之所有檔案的清單方塊。 可惜的是，IDE 不知道使用者可能取得的所有檔案的確切清單，只有外掛程式具有這份清單。 如果其他使用者已將檔案新增至原始程式碼控制專案，這些檔案應該會出現在清單中，但 IDE 不知道它們。 IDE 會建立其認為使用者可以取得的檔案清單。 它會在向使用者顯示此清單之前呼叫 SccPopulateList， [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` 讓原始檔控制外掛程式有機會從清單中新增及刪除檔案。  
  
## <a name="signature"></a>簽章  
 原始檔控制外掛程式會使用下列原型來呼叫 IDE 執行的函式，以修改清單：  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>參數  
 pvCallerData  
 `pvCallerData`呼叫端傳遞的參數 (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md)。 原始檔控制外掛程式應該不會假設此參數的內容。  
  
 fAddRemove  
 如果 `TRUE` `lpFileName` 為，則是應該加入檔案清單中的檔案。 如果 `FALSE` `lpFileName` 為，則是應該從檔案清單中刪除的檔案。  
  
 nStatus  
  (的狀態組合的狀態 `lpFileName` `SCC_STATUS` ; 如需詳細資料，請參閱檔案 [狀態碼](../extensibility/file-status-code-enumerator.md)) 。  
  
 lpFileName  
 要從清單中新增或刪除之檔案名的完整目錄路徑。  
  
## <a name="return-value"></a>傳回值  
  
|值|描述|  
|-----------|-----------------|  
|`TRUE`|外掛程式可以繼續呼叫此函數。|  
|`FALSE`|IDE 端 (發生問題，例如記憶體不足的情況) 。 外掛程式應該會停止操作。|  
  
## <a name="remarks"></a>備註  
 針對原始檔控制外掛程式想要在檔案清單中新增或刪除的每個檔案，它會呼叫此函式，並傳入 `lpFileName` 。 `fAddRemove`旗標表示要新增至清單的新檔案，或要刪除的舊檔案。 參數會提供檔案的 `nStatus` 狀態。 當 SCC 外掛程式完成新增和刪除檔案時，它會從 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 呼叫傳回。  
  
> [!NOTE]
> `SCC_CAP_POPULATELIST`Visual Studio 需要功能位。  
  
## <a name="see-also"></a>另請參閱  
 [IDE 所執行的回呼函數](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)
