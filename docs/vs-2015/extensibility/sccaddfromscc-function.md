---
title: SccAddFromScc 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 346a036d38c7ee86daf30320c5f454f9e807f7d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943593"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函數可讓使用者瀏覽已在原始檔控制系統中的檔案，並接著讓這些檔案的部分目前的專案。 比方說，此函式可以取得常見的標頭檔到目前的專案而不複製檔案。 傳回陣列的檔案， `lplpFileNames`，包含的使用者想要新增至 IDE 專案的檔案清單。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 lpnFiles  
 [in、 out]在新增的檔案數目的緩衝區。 (這是`NULL`如果指向的記憶體所`lplpFileNames`將被釋放。 請參閱 < 備註 > 一如需詳細資訊）。  
  
 lplpFileNames  
 [in、 out]沒有目錄路徑的所有檔案名稱的指標陣列。 這個陣列配置和釋出原始檔控制外掛程式。 如果`lpnFiles`= 1，`lplpFileNames`不是`NULL`，在陣列中的第一個名稱所指的`lplpFileNames`包含目的地資料夾。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|檔案已順利位於，並加入至專案。|  
|SCC_I_OPERATIONCANCELED|不會影響已取消作業。|  
|SCC_I_RELOADFILE|必須重新載入檔案或專案。|  
  
## <a name="remarks"></a>備註  
 IDE 會呼叫此函式。 如果原始檔控制外掛程式支援指定的本機目的資料夾，IDE 會傳遞`lpnFiles`= 1，並將傳遞到本機資料夾名稱`lplpFileNames`。  
  
 時呼叫`SccAddFromScc`函式傳回時，外掛程式已指派值，以`lpnFiles`並`lplpFileNames`，視需要的檔案名稱陣列配置記憶體 (請注意，此配置會取代中的指標`lplpFileNames`)。 原始檔控制外掛程式負責將所有檔案都放到使用者的目錄，或指定的指定資料夾中。 然後，IDE 會將檔案加入 IDE 專案。  
  
 最後，IDE 會呼叫此函式第二次，並傳遞`NULL`針對`lpnFiles`。 這會解譯為特殊的訊號，原始檔控制外掛程式，以釋出配置給檔案名稱陣列中的記憶體 `lplpFileNames``.`  
  
 `lplpFileNames` 是`char ***`指標。 原始檔控制外掛程式將放置的檔案名稱，藉以在此 api 的標準方式傳遞清單的指標陣列的指標。  
  
> [!NOTE]
>  VSSCI API 的初始版本未提供一個方法來指示加入之檔案的目標專案。 為了完成此的語意`lplpFIleNames`參數已經強化，可讓 in/out 參數，而不是一個 output 參數。 如果只指定單一檔案，也就是值所指向`lpnFiles`= 1，則第一個項目`lplpFileNames`包含目標資料夾。 若要使用這些新的語意，IDE 會呼叫`SccSetOption`函式搭配`nOption`參數設為`SCC_OPT_SHARESUBPROJ`。 如果原始檔控制外掛程式不支援語意，它會傳回`SCC_E_OPTNOTSUPPORTED`。 執行使用的是停用**從原始檔控制新增**功能。 如果外掛程式支援**從原始檔控制新增**功能 (`SCC_CAP_ADDFROMSCC`)，則它必須支援新的語意，並傳回`SCC_I_SHARESUBPROJOK`。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
