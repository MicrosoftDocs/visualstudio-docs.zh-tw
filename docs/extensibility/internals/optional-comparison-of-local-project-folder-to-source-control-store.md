---
title: 比較原始檔控制存放區至專案資料夾 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>原始檔控制存放區的本機專案資料夾的選擇性比較
在原始檔控制外掛程式 API 1.2 局部的專案資料夾與原始檔控制之間的比較透過函式的使用[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)。  
  
 內**方案總管 中**，如果已選取的資料夾，而不是個別檔案，**比較版本**快顯功能表叫用新[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)和[SccDirDiff](../../extensibility/sccdirdiff-function.md)在原始檔控制外掛程式。  
  
## <a name="new-capability-flags"></a>新的功能旗標  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新的函式  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`之前呼叫函式`SccDirDiff`判斷是否為原始檔控制的工作目錄。 `SccDirDiff`函式會顯示目前的本機目錄和對應的原始檔控制資料夾之間的差異。 此命令會要求的原始檔控制外掛程式，以顯示變更清單的目錄。 原始檔控制外掛程式提供它自己的 UI 來顯示差異。  
  
> [!NOTE]
>  此函式會使用相同的命令旗標，表示[SccDiff](../../extensibility/sccdiff-function.md)。 做為原始檔控制外掛程式提供者，您可以選擇不支援目錄的 「 快速差異 」 作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 版本 1.2 的新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)