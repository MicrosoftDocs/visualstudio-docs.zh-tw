---
title: "POPLISTFUNC |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc15af65c6541df5ef77a3bdc85ee0e59fa20991
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
此回呼會提供給[SccPopulateList](../extensibility/sccpopulatelist-function.md) ide 而且由原始檔控制外掛程式用來更新檔案或目錄的清單 (也提供給`SccPopulateList`函式)。  
  
 當使用者選擇**取得**命令在 IDE 中，IDE 會顯示清單方塊的使用者也可以取得的所有檔案。 不幸的是，IDE 不知道使用者可能會收到; 的所有檔案的清單只有外掛程式都具有此清單。 如果其他使用者已將檔案加入原始程式碼控制項專案，這些檔案應該會出現在清單中，但 IDE 不知道它們。 IDE 會建置一份其認定使用者也可以取得的檔案。 向使用者顯示此清單之前，它會呼叫[SccPopulateList](../extensibility/sccpopulatelist-function.md) `,`提供原始檔控制外掛程式有機會新增，並從清單中刪除檔案。  
  
## <a name="signature"></a>簽章  
 原始檔控制外掛程式會藉由呼叫 IDE 實作函式具有下列原型修改清單：  
  
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
 `pvCallerData`參數傳遞至呼叫端 (IDE) [SccPopulateList](../extensibility/sccpopulatelist-function.md)。 原始檔控制外掛程式，應該假設任何有關此參數的內容。  
  
 fAddRemove  
 如果`TRUE`，`lpFileName`是應加入的檔案清單的檔案。 如果`FALSE`，`lpFileName`是應該從檔案清單中刪除的檔案。  
  
 nStatus  
 狀態`lpFileName`(的組合`SCC_STATUS`位元，請參閱 <<c4> [ 檔案狀態碼](../extensibility/file-status-code-enumerator.md)如需詳細資訊)。  
  
 lpFileName  
 要加入或從清單中刪除的檔案名稱的完整目錄路徑。  
  
## <a name="return-value"></a>傳回值  
  
|值|描述|  
|-----------|-----------------|  
|`TRUE`|外掛程式可以繼續呼叫這個函式。|  
|`FALSE`|在 IDE 端 （例如不足的記憶體的情況下） 已有問題。 外掛程式應該停止的作業。|  
  
## <a name="remarks"></a>備註  
 原始檔控制外掛程式想要加入或刪除檔案清單中的每個檔案，它會呼叫這個函式，並傳入`lpFileName`。 `fAddRemove`旗標指出新的檔案新增至清單或刪除舊的檔案。 `nStatus`參數會提供檔案的狀態。 當外掛程式 SCC 完成加入和刪除檔案時，它會傳回[SccPopulateList](../extensibility/sccpopulatelist-function.md)呼叫。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST`功能個位元都是必要的 Visual Studio。  
  
## <a name="see-also"></a>請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)