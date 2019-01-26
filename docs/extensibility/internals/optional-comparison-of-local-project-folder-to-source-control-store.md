---
title: 比較專案資料夾與來源控制存放區 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01ccbc50f9b88d2263f4fca913b78921ce88a4a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922151"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>本機專案資料夾與原始檔控制存放區的選擇性比較
在原始檔控制外掛程式 API 1.2 本機專案資料夾與原始檔控制之間的比較作業透過使用函式[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)並[SccDirDiff](../../extensibility/sccdirdiff-function.md)。  
  
 內**方案總管**，如果已選取的資料夾，而不是個別的檔案，**比較版本**快顯功能表叫用的新[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)在原始檔控制外掛程式。  
  
## <a name="new-capability-flags"></a>新的功能旗標  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新的函式  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`函式之前，會呼叫`SccDirDiff`判斷是否為原始檔控制的工作目錄。 `SccDirDiff`函式會顯示目前的本機目錄與對應的原始檔控制資料夾之間的差異。 此命令會要求原始檔控制外掛程式，以顯示變更的清單目錄。 原始檔控制外掛程式提供它自己的 UI 來顯示差異。  
  
> [!NOTE]
>  此函式會使用相同的命令旗標，作為[SccDiff](../../extensibility/sccdiff-function.md)。 做為原始檔控制外掛程式提供者，您可以選擇不支援目錄的 「 快速 diff"作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)