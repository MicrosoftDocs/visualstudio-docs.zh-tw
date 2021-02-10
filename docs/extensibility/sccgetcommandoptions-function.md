---
title: SccGetCommandOptions 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1f465e6709932cd89794c5c0558d608fadd2a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965196"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 函式
此函數會提示使用者提供指定命令的 advanced 選項。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 iCommand

在要求 advanced 選項的命令 (參閱 [命令程式碼](../extensibility/command-code-enumerator.md) 以取得可能的值) 。

 ppvOptions

在選項結構 (也可以 `NULL`) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_I_ADV_SUPPORT|原始檔控制外掛程式支援命令的 advanced 選項。|
|SCC_I_OPERATIONCANCELED|使用者取消了原始檔控制外掛程式的 [ **選項** ] 對話方塊。|
|SCC_E_OPTNOTSUPPORTED|原始檔控制外掛程式不支援這項操作。|
|SCC_E_ISCHECKEDOUT|無法在目前簽出的檔案上執行這項作業。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR|模糊失敗。|

## <a name="remarks"></a>備註
 IDE 第一次呼叫此函式， `ppvOptions` = `NULL` 以判斷原始檔控制外掛程式是否支援指定命令的 advanced options 功能。 如果外掛程式支援該命令的功能，則當使用者要求 advanced 選項時，IDE 會再次呼叫這個函式 (通常會實作為對話方塊中的 [ **advanced** ] 按鈕) 並提供指向指標的非 Null 指標 `ppvOptions` `NULL` 。 外掛程式會將使用者指定的任何 advanced 選項儲存在私用結構中，並在中傳回該結構的指標 `ppvOptions` 。 此結構接著會傳遞給所有其他需要知道的原始檔控制外掛程式 API 函式，包括後續的函式呼叫 `SccGetCommandOptions` 。

 範例可能有助於說明這種情況。

 使用者選擇 [ **取得** ] 命令，IDE 會顯示 [ **取得** ] 對話方塊。 IDE 會呼叫 `SccGetCommandOptions` 函數， `iCommand` 並將設定為 `SCC_COMMAND_GET` ，並 `ppvOptions` 將設定為 `NULL` 。 原始檔控制外掛程式會解釋這個問題：「您是否有此命令的任何 advanced 選項？」。 如果外掛程式傳回 `SCC_I_ADV_SUPPORT` ，IDE 會在其 [ **Get** ] 對話方塊中顯示 [ **Advanced** ] 按鈕。

 當使用者第一次按一下 [ **Advanced** ] 按鈕時，IDE 會再次呼叫函 `SccGetCommandOptions` 式，這次會以非指向指標的方式呼叫函式 `NULL``ppvOptions` `NULL` 。 外掛程式會顯示自己的 [ **取得選項** ] 對話方塊、提示使用者提供資訊、將該資訊放入自己的結構，然後在中傳回該結構的指標 `ppvOptions` 。

 如果使用者在同一個對話方塊中再次按一下 [ **Advanced** ]，IDE 就會再次呼叫函式 `SccGetCommandOptions` 而不會變更 `ppvOptions` ，以便將結構傳回至外掛程式。 這可讓外掛程式將其對話方塊重新初始化為使用者先前設定的值。 外掛程式會在傳回之前修改結構。

 最後，當使用者在 IDE 的 [**取得**] 對話方塊中按一下 **[確定**] 時，ide 會呼叫 [SccGet](../extensibility/sccget-function.md)，並傳遞傳回的結構， `ppvOptions` 其中包含 advanced 選項。

> [!NOTE]
> `SCC_COMMAND_OPTIONS`當 IDE 顯示 [**選項**] 對話方塊，可讓使用者設定控制整合運作方式的喜好設定時，就會使用此命令。 如果原始檔控制外掛程式想要提供自己的 [喜好設定] 對話方塊，它可以從 IDE 的 [喜好設定] 對話方塊中的 [ **Advanced** ] 按鈕顯示它。 此外掛程式僅負責取得和保存這項資訊;IDE 不會使用或修改它。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [命令碼](../extensibility/command-code-enumerator.md)
