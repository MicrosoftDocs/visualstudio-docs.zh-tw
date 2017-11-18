---
title: "Idiaenumsourcefiles:: Clone |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 778152f721222efab46f0bf10a53f808abe4be3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
建立列舉值，包含目前的列舉值的列舉型別狀態相同。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Clone (   
   IDiaEnumSourceFiles** ppenum  
);  
```  
  
#### <a name="parameters"></a>參數  
 ppenum  
 [out]傳回[IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)物件，其中包含列舉值重複。 來源檔案不被重複的列舉值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)