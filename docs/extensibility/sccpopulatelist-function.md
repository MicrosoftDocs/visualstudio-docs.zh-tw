---
description: 此函式會更新特定原始檔控制命令的檔案清單，並在所有指定的檔案上提供原始檔控制狀態。
title: SccPopulateList 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ae531b4be3406c38180183037695a2320b372b14
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056528"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函式
此函式會更新特定原始檔控制命令的檔案清單，並在所有指定的檔案上提供原始檔控制狀態。

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

在原始檔控制外掛程式內容結構。

 nCommand

在將套用至陣列中所有檔案的原始檔控制命令 `lpFileNames` (參閱命令程式 [代碼](../extensibility/command-code-enumerator.md) ，以取得可能的命令清單) 。

 nFiles

在陣列中的檔案數目 `lpFileNames` 。

 lpFileNames

在IDE 已知的檔案名陣列。

 pfnPopulate

在要呼叫以新增和移除檔案的 IDE 回呼函式 (如需詳細資料) ，請參閱 [POPLISTFUNC](../extensibility/poplistfunc.md) 。

 pvCallerData

在要原封不動地傳遞給回呼函式的值。

 lpStatus

[in，out]原始檔控制外掛程式的陣列，用來傳回每個檔案的狀態旗標。

 fOptions

在命令旗標 (查看 [特定命令所使用之位旗標](../extensibility/bitflags-used-by-specific-commands.md) 的「PopulateList 旗標」一節，以取得詳細資料) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 此函式會檢查檔案清單中的目前狀態。 它會使用 `pfnPopulate` 回呼函式，在檔案不符合的條件時通知呼叫端 `nCommand` 。 例如，如果命令為， `SCC_COMMAND_CHECKIN` 而且清單中的檔案尚未簽出，則會使用回呼來通知呼叫者。 有時候，原始檔控制外掛程式可能會找到其他可能是命令的一部分的檔案，並加以新增。 例如，這可讓 Visual Basic 使用者簽出其專案所使用但未出現在 Visual Basic 專案檔中的 .bmp 檔案。 使用者選擇 IDE 中的 **Get** 命令。 IDE 會顯示它認為使用者可以取得的所有檔案清單，但在顯示清單之前，會呼叫此函式， `SccPopulateList` 以確保顯示的清單是最新的。

## <a name="example"></a>範例
 IDE 會建立其認為使用者可以取得的檔案清單。 它會在顯示這份清單之前呼叫函 `SccPopulateList` 式，讓原始檔控制外掛程式有機會從清單中新增及刪除檔案。 外掛程式會藉由呼叫指定的回呼函數來修改清單 (如需詳細資料，請參閱 [POPLISTFUNC](../extensibility/poplistfunc.md)) 。

 外掛程式會繼續呼叫函式 `pfnPopulate` ，該函式會新增和刪除檔案，直到完成，然後從函式傳回 `SccPopulateList` 。 然後，IDE 可以顯示其清單。 `lpStatus`陣列代表 IDE 傳入的原始清單中的所有檔案。 外掛程式除了使用回呼函式之外，還會填入所有這些檔案的狀態。

> [!NOTE]
> 原始檔控制外掛程式一律會有直接從這個函式傳回的選項，讓清單保持不運作。 如果外掛程式會執行此函式，它可以藉由設定 `SCC_CAP_POPULATELIST` 第一次呼叫 [SccInitialize](../extensibility/sccinitialize-function.md)的功能位來指出這一點。 根據預設，外掛程式應該一律假設傳入的所有專案都是檔案。 但是，如果 IDE 在 `SCC_PL_DIR` 參數中設定旗標 `fOptions` ，則所有傳入的專案都會被視為目錄。 外掛程式應加入目錄中的所有檔案。 IDE 永遠不會傳入檔案和目錄的混合。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [命令碼](../extensibility/command-code-enumerator.md)
