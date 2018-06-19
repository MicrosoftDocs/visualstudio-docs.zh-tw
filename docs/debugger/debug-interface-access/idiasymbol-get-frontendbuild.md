---
title: 'Idiasymbol:: Get_frontendbuild |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bc674f99f858add7aee40b7d20d150052068139
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464907"
---
# <a name="idiasymbolgetfrontendbuild"></a>IDiaSymbol::get_frontEndBuild
擷取前端組建編號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_frontEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回前端組建編號。 請參閱＜備註＞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="remarks"></a>備註  
 編譯器通常由兩個主要項目所組成： 前端 （剖析器），用來處理來源的程式碼剖析為中繼格式，以及的後端 （程式碼產生器），它會將中繼格式轉換成組件。 是很常見的前端有後端的版本不同的位置。  
  
 前端或後端版本號碼是三個部分組成：\<主要 >。\<次要 >。\<建置 >，其中\<主要 > 是主要版本號碼，\<次要 > 是次要版本號碼，和\<建置 > 是的組建編號。 例如，13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|標頭：|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)