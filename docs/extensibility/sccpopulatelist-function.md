---
title: SccPopulateList 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720863"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函式
此函式會更新特定原始檔控制命令的檔案清單，並提供所有指定檔案的原始檔控制狀態。

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
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 nCommand

在將套用至 `lpFileNames` 陣列中所有檔案的原始檔控制命令（如需可能的命令清單，請參閱[命令程式碼](../extensibility/command-code-enumerator.md)）。

 n

在@No__t_0 陣列中的檔案數目。

 lpFileNames

在IDE 已知的檔案名陣列。

 pfnPopulate

在要呼叫來新增和移除檔案的 IDE 回呼函式（如需詳細資訊，請參閱[POPLISTFUNC](../extensibility/poplistfunc.md) ）。

 pvCallerData

在要原封不動地傳遞至回呼函式的值。

 lpStatus

[in、out]原始檔控制外掛程式的陣列，用來傳回每個檔案的狀態旗標。

 fOptions

在命令旗標（請參閱[特定命令所使用之位旗標](../extensibility/bitflags-used-by-specific-commands.md)的 "PopulateList flags" 一節以取得詳細資料）。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_NONSPECIFICERROR|不明確的失敗。|

## <a name="remarks"></a>備註
 此函式會檢查檔案的清單，以瞭解其目前的狀態。 當檔案不符合 `nCommand` 的準則時，它會使用 `pfnPopulate` 回呼函數來通知呼叫者。 例如，如果命令是 `SCC_COMMAND_CHECKIN` 且清單中的檔案未簽出，則會使用回呼來通知呼叫者。 有時候，原始檔控制外掛程式可能會尋找可能屬於命令一部分的其他檔案，並加以新增。 例如，這可讓 Visual Basic 的使用者簽出其專案所使用但未出現在 Visual Basic 專案檔案中的 .bmp 檔案。 使用者在 IDE 中選擇**Get**命令。 IDE 會顯示其認為使用者可以取得的所有檔案清單，但在顯示清單之前，會呼叫 `SccPopulateList` 函式，以確定要顯示的清單是最新的。

## <a name="example"></a>範例
 IDE 會建立它認為使用者可以取得的檔案清單。 在顯示此清單之前，它會呼叫 `SccPopulateList` 函式，讓原始檔控制外掛程式有機會新增和刪除清單中的檔案。 外掛程式會藉由呼叫指定的回呼函數來修改清單（如需詳細資訊，請參閱[POPLISTFUNC](../extensibility/poplistfunc.md) ）。

 外掛程式會繼續呼叫 `pfnPopulate` 函式，此函式會新增和刪除檔案，直到完成，然後再從 `SccPopulateList` 函式傳回為止。 然後，IDE 就可以顯示其清單。 @No__t_0 陣列代表 IDE 傳入的原始清單中的所有檔案。 外掛程式會填入所有這些檔案的狀態，並使用回呼函數。

> [!NOTE]
> 原始檔控制外掛程式一律可以選擇直接從這個函式傳回，讓清單保持不存在。 如果外掛程式會執行此函式，則可以在第一次呼叫[SccInitialize](../extensibility/sccinitialize-function.md)時設定 `SCC_CAP_POPULATELIST` 功能位來指出這一點。 根據預設，外掛程式應該會假設傳入的所有專案都是檔案。 不過，如果 IDE 在 `fOptions` 參數中設定 `SCC_PL_DIR` 旗標，則所有傳入的專案都會被視為目錄。 外掛程式應該加入所有屬於目錄中的檔案。 IDE 永遠不會傳入檔案和目錄的混合。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [命令碼](../extensibility/command-code-enumerator.md)