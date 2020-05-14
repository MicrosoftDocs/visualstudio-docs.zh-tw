---
title: POPLISTFUNC |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702068"
---
# <a name="poplistfunc"></a>POPLISTFUNC
此回檔由 IDE 提供給[SccPopulateList,](../extensibility/sccpopulatelist-function.md)原始程式碼管理外掛程式用於更新檔或`SccPopulateList`目錄的清單(也提供給函數)。

 當使用者在 IDE 中選擇**Get**命令時,IDE 將顯示使用者可以獲取的所有檔案的清單框。 遺憾的是,IDE 不知道使用者可能獲得的所有文件的確切清單;只有外掛程式有此清單。 如果其他使用者將檔添加到原始程式碼管理專案,這些檔應出現在清單中,但IDE 不知道它們。 IDE 生成它認為使用者可以獲取的檔的清單。 在向使用者顯示此清單之前,它會調用[SccPopulateList,](../extensibility/sccpopulatelist-function.md)`,`使原始程式碼管理外掛程式有機會從清單中添加和刪除檔。

## <a name="signature"></a>簽章
 原始程式碼管理外掛程式透過使用以下原型呼叫 IDE 實現函數來修改清單:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>參數
 pvCallerData`pvCallerData`調用方 (IDE) 傳遞給[SccpopulateList 的](../extensibility/sccpopulatelist-function.md)參數。 原始程式碼管理外掛程式不應假定此參數的內容。

 fAddRemove `TRUE` `lpFileName` If , 是應添加到檔案清單中的檔。 如果`FALSE``lpFileName`是應從檔案清單中刪除的檔案。

 n`lpFileName`狀態`SCC_STATUS`狀態( 位的組合;有關詳細資訊,請參閱[檔案狀態代碼](../extensibility/file-status-code-enumerator.md))。

 lpFileName 檔案名的完整目錄路徑,以便從清單中添加或刪除。

## <a name="return-value"></a>傳回值

|值|描述|
|-----------|-----------------|
|`TRUE`|外掛程式可以繼續調用此功能。|
|`FALSE`|IDE 端出現問題(如記憶體不足情況)。 外掛程式應停止操作。|

## <a name="remarks"></a>備註
 對於原始碼管理外掛程式要加入檔案清單中或移除的每個檔案,它將呼叫此函數,傳入`lpFileName`。 這個`fAddRemove`標示加入清單的新檔案或要刪除的舊檔案。 參數`nStatus`提供文件的狀態。 當 SCC 外掛程式完成添加和刪除檔後,它將從[SccPopulateList](../extensibility/sccpopulatelist-function.md)呼叫返回。

> [!NOTE]
> 可視化`SCC_CAP_POPULATELIST`工作室需要功能位。

## <a name="see-also"></a>另請參閱
- [IDE 實作的回檔](../extensibility/callback-functions-implemented-by-the-ide.md)
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [檔案狀態代碼](../extensibility/file-status-code-enumerator.md)
