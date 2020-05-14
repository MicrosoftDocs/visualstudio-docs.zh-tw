---
title: 放大縮小字型功能 放大縮小字型功能微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700537"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函式
此函數更新特定原始程式碼管理命令的檔案清單,並在所有給定檔上提供原始程式碼管理狀態。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 nCommand

[在]將應用於`lpFileNames`數位中的所有檔的原始程式碼控制命令(有關可能的命令清單,請參閱[命令代碼](../extensibility/command-code-enumerator.md))。

 n 檔案

[在]陣列中`lpFileNames`的檔案數。

 lpFile 名稱

[在]IDE 已知的檔名陣列。

 pfn 填充

[在]用於呼叫以添加和刪除檔的IDE回檔函數(有關詳細資訊,請參閱[POPLISTFUNC)。](../extensibility/poplistfunc.md)

 pvCallerData

[在]要傳遞給回調函數的值保持不變。

 lp狀態

[進出]源控件外掛程式的陣列,用於返回每個文件的狀態標誌。

 fOptions

[在]命令標誌(有關詳細資訊,請參閱[特定命令使用的位標誌的](../extensibility/bitflags-used-by-specific-commands.md)"填充清單標誌"部分)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 此函數檢查檔案清單的當前狀態。 當檔與`pfnPopulate`的條件`nCommand`不匹配時,它使用回調函數通知調用方。 例如,如果命令是`SCC_COMMAND_CHECKIN`,並且清單中的檔未簽出,則回調用於通知調用方。 有時,原始程式碼管理外掛程式可能會找到其他文件,這些檔可能是命令的一部分,並添加它們。 例如,這允許 Visual Basic 使用者簽出其專案使用的 .bmp 檔,但不顯示在 Visual Basic 專案檔中。 使用者在 IDE 中選擇 **「獲取**」命令。 IDE 將顯示它認為使用者可以獲取的所有檔案的清單,但在顯示清單之前,將調用`SccPopulateList`該 函數以確保要顯示的清單是最新的。

## <a name="example"></a>範例
 IDE 生成它認為使用者可以獲取的檔案清單。 在顯示此清單之前,它會調用`SccPopulateList`該函數,使原始程式碼管理外掛程式有機會從清單中添加和刪除檔。 外掛程式透過調用給定的回調函數來修改清單(有關詳細資訊,請參閱[POPLISTFUNC)。](../extensibility/poplistfunc.md)

 外掛程式繼續呼`pfnPopulate`叫 函數,該函數添加和刪除檔,直到它完成,然後從`SccPopulateList`函數返回。 然後,IDE 可以顯示其清單。 陣列`lpStatus`表示 IDE 傳入的原始清單中的所有檔。 除了使用回調功能外,外掛程式還填充所有這些文件的狀態。

> [!NOTE]
> 原始程式碼管理外掛程式始終可以選擇立即從此函數返回,使清單保留為現在。 如果外掛程式實現此函數,它可以通過在[Scc 初始化](../extensibility/sccinitialize-function.md)的第一`SCC_CAP_POPULATELIST`個調用中設置功能位標誌來指示這一點。 預設情況下,外掛程式應始終假定傳入的所有專案都是檔。 但是,如果 IDE`SCC_PL_DIR``fOptions`在 參數中設置標誌,則傳入的所有項都將被視為目錄。 外掛程式應添加屬於目錄中的所有檔。 IDE 永遠不會傳遞檔和目錄的混合。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [命令碼](../extensibility/command-code-enumerator.md)
