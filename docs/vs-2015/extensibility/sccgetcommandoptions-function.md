---
title: SccGetCommandOptions 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7838ffaccbef6e4bdcde97313f118e7aa13b4d1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487318"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccGetCommandOptions 函式](https://docs.microsoft.com/visualstudio/extensibility/sccgetcommandoptions-function)。  
  
此函數會提示使用者提供針對特定命令的進階選項。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 iCommand  
 [in]要求的進階的選項的命令 (請參閱[的指令碼](../extensibility/command-code-enumerator.md)可能的值)。  
  
 ppvOptions  
 [in]選項的結構 (也可以是`NULL`)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_I_ADV_SUPPORT|原始檔控制外掛程式支援命令的進階的選項。|  
|SCC_I_OPERATIONCANCELED|使用者已取消原始檔控制隨插即用單元的**選項** 對話方塊。|  
|SCC_E_OPTNOTSUPPORTED|原始檔控制外掛程式不支援這項作業。|  
|SCC_E_ISCHECKEDOUT|無法執行這項作業目前已簽出檔案。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 IDE 與第一次呼叫此函式`ppvOptions` = `NULL`以判斷原始檔控制外掛程式是否支援指定命令的進階的選項的功能。 如果外掛程式支援此功能會針對該命令，IDE 會呼叫此函數一次使用者要求的進階的選項時 (通常實作為**進階**在對話方塊中的按鈕)，並提供非NULL指標`ppvOptions` ，以指到`NULL`指標。 外掛程式會儲存在私用的結構中的使用者所指定的任何進階的選項，並傳回在該結構的指標`ppvOptions`。 此結構會傳遞至所有其他原始檔控制外掛程式 API 函式，需要了解，包括後續呼叫`SccGetCommandOptions`函式。  
  
 範例可能有助於釐清這種情況。  
  
 使用者選擇**取得**命令，IDE 就會顯示**取得** 對話方塊。 IDE 呼叫`SccGetCommandOptions`函式搭配`iCommand`設為`SCC_COMMAND_GET`並`ppvOptions`設定為`NULL`。 這解譯的原始檔控制外掛程式的問題，「 您有任何進階的選項，此命令？ 」 如果外掛程式傳回`SCC_I_ADV_SUPPORT`，IDE 會顯示**進階**按鈕及其**取得** 對話方塊。  
  
 第一次使用者按一下**進階** 按鈕，再次呼叫 IDE`SccGetCommandOptions`函式，這次使用非`NULL``ppvOptions`，以指到`NULL`指標。 外掛程式會顯示自己**取得選項** 對話方塊中，會提示使用者輸入資訊，將該資訊到其本身的結構，並傳回在該結構的指標`ppvOptions`。  
  
 如果使用者按一下**進階**再次在相同的對話方塊中，IDE 會呼叫`SccGetCommandOptions`函式，而不變更`ppvOptions`，如此一來，結構傳回給外掛程式。 這可讓外掛程式，以重新初始化其使用者先前已設定的值 對話方塊。 外掛程式會修改結構，然後傳回。  
  
 最後，當使用者按一下 **[確定]** 在 IDE 中**取得** 對話方塊中，IDE 會呼叫[SccGet](../extensibility/sccget-function.md)，傳遞結構中傳回`ppvOptions`包含進階的選項。  
  
> [!NOTE]
>  此命令`SCC_COMMAND_OPTIONS`IDE 會顯示時，會使用**選項**對話方塊，讓使用者設定控制整合的運作方式的喜好設定。 如果原始檔控制外掛程式想要提供自己的喜好設定 對話方塊中，它可以顯示從**進階**IDE 的 喜好設定 對話方塊中的按鈕。 外掛程式只負責取得並保存這項資訊;IDE 不會使用它，或修改它。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [命令碼](../extensibility/command-code-enumerator.md)

