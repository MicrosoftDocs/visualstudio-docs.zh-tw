---
title: "SccAddFromScc 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFromScc
helpviewer_keywords: SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5027e765e12ff483a9a27795990f0ddfbb479a5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc 函式
此函式可讓使用者瀏覽已在原始檔控制系統中的檔案，之後將這些檔案目前的專案。 例如，此函式可以取得常見的標頭檔到目前的專案而不複製檔案。 傳回陣列的檔案， `lplpFileNames`，包含的使用者想要新增至 IDE 專案的檔案清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpnFiles  
 [in、 out]緩衝中加入的檔案數目。 (這是`NULL`如果所指向的記憶體`lplpFileNames`會釋出。 請參閱 < 備註 > 以取得詳細資料）。  
  
 lplpFileNames  
 [in、 out]沒有目錄路徑的所有檔案名稱的指標陣列。 這個陣列配置和釋出原始檔控制外掛程式。 如果`lpnFiles`= 1 和`lplpFileNames`不`NULL`，所指陣列中的名字`lplpFileNames`包含目的地資料夾。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|檔案已成功位於而且加入至專案。|  
|SCC_I_OPERATIONCANCELED|不會影響已取消作業。|  
|SCC_I_RELOADFILE|需要重新載入檔案或專案。|  
  
## <a name="remarks"></a>備註  
 IDE 會呼叫此函式。 如果原始檔控制外掛程式支援指定的本機目的資料夾，IDE 會將傳遞`lpnFiles`= 1，並傳遞到本機資料夾名稱`lplpFileNames`。  
  
 當呼叫`SccAddFromScc`函式傳回時，外掛程式已指派值給`lpnFiles`和`lplpFileNames`，為檔案名稱陣列，視需要配置記憶體 (請注意此配置會取代中的指標`lplpFileNames`)。 原始檔控制外掛程式負責將所有檔案都放入使用者的目錄或指定的目的地資料夾中。 然後，IDE 會將檔案加入 IDE 專案。  
  
 最後，IDE 會呼叫此函式中傳遞的第二次`NULL`如`lpnFiles`。 這會解譯為特殊的訊號，原始檔控制外掛程式，以釋放配置的檔案名稱陣列中的記憶體`lplpFileNames``.`  
  
 `lplpFileNames`是`char ***`指標。 將檔案名稱，藉以在此 api 的標準方式傳遞清單的指標陣列的指標放在原始檔控制外掛程式。  
  
> [!NOTE]
>  初始 VSSCI API 版本未提供一個方法來指示加入的檔案的目標專案。 若要完成此的語意`lplpFIleNames`參數已增強為方便輸入/輸出參數，而不是輸出參數。 如果只指定單一檔案，也就是指之值`lpnFiles`= 1，則第一個項目`lplpFileNames`包含目標資料夾。 若要使用這些新的語意，IDE 呼叫`SccSetOption`函式與`nOption`參數設定為`SCC_OPT_SHARESUBPROJ`。 如果原始檔控制外掛程式不支援語意，它會傳回`SCC_E_OPTNOTSUPPORTED`。 執行這樣的停用使用**從原始檔控制加入**功能。 如果外掛程式支援**從原始檔控制加入**功能 (`SCC_CAP_ADDFROMSCC`)，則必須支援新的語意，並傳回`SCC_I_SHARESUBPROJOK`。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)