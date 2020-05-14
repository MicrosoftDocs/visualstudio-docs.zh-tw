---
title: SccGet命令選項功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700826"
---
# <a name="sccgetcommandoptions-function"></a>SccGet命令選項功能
此函數提示使用者為給定命令提供高級選項。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 iCommand

[在]請求進階選項的命令(有關可能的值,請參閱[命令代碼](../extensibility/command-code-enumerator.md))。

 ppvOptions

[在]選項結構(也可以為`NULL`)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功。|
|SCC_I_ADV_SUPPORT|源代碼管理外掛程式支援命令的進階選項。|
|SCC_I_OPERATIONCANCELED|使用者取消了原始碼管理外掛程式的 **「選項」** 對話框。|
|SCC_E_OPTNOTSUPPORTED|原始程式碼管理外掛程式不支援此操作。|
|SCC_E_ISCHECKEDOUT|無法對當前簽出的檔執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR|非特異性故障。|

## <a name="remarks"></a>備註
 IDE`ppvOptions`=`NULL`首次調用此函數,以確定原始程式碼管理外掛程式是否支援指定命令的進階選項功能。 如果外掛程式確實支援該命令的功能,則當使用者請求高級選項(通常在對話方塊中作為**進階**按鈕實現`ppvOptions`)並為`NULL`該指標 提供非 NULL 指標時,IDE 將再次呼叫此函數。 該外掛程式將使用者指定的任何高級選項存儲在私有結構中,並在中返回指向該結構`ppvOptions`的指標。 然後,此結構將傳遞給所有其他原始程式碼管理外掛程式 API 函數,這些函數需要瞭解它,包括隨後`SccGetCommandOptions`對函數的調用。

 一個例子可能有助於澄清這種情況。

 使用者選擇 **「獲取」** 命令,IDE 將顯示 **「獲取」** 對話方塊。 IDE 調用設置`SccGetCommandOptions``iCommand``SCC_COMMAND_GET`為`ppvOptions`和`NULL`設置為的函數。 原始程式碼管理外掛程式將此解釋為「您對此命令是否有任何高級選項? 如果外掛程式`SCC_I_ADV_SUPPORT`傳回 ,IDE 在其 **「獲取」** 對話框中顯示**一個高級**按鈕。

 使用者首次按下 **「高級」** 按鈕時,IDE 將`SccGetCommandOptions`再次調用 該函數,這`NULL``ppvOptions``NULL`一次使用指向指標的非函數。 該外掛程式顯示其自己的 **「獲取選項」** 對話框,提示使用者提供資訊,將該資訊放入其自己的結構,並在中返回指向`ppvOptions`該結構的指標。

 如果使用者在同一對話方塊中再次按下 **「高級」,IDE**將`SccGetCommandOptions`再次調用 該`ppvOptions`函數而不更改 ,以便結構傳回外掛程式。 這使外掛程式能夠將其對話框重新初始化到使用者以前設置的值。 外掛程式在返回之前修改就地的結構。

 最後,當使用者單擊 IDE 的 **「獲取」** 對話方塊中的 **「確定」** 時,IDE 將呼叫`ppvOptions`[SccGet,](../extensibility/sccget-function.md)傳遞傳回的結構 ,其中包含進階選項。

> [!NOTE]
> 當`SCC_COMMAND_OPTIONS`IDE 顯示**選項**對話方塊,允許使用者設置控制整合工作方式的首選項時,將使用該命令。 如果原始程式碼管理外掛程式想要提供自己的首選項對話框,則可以從 IDE 首選項對話方塊中的 **「進階」** 按鈕顯示它。 外掛程式完全負責獲取和保留此資訊;IDE 不使用或修改它。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [命令代碼](../extensibility/command-code-enumerator.md)
