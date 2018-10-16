---
title: 本機專案資料夾與來源控制存放區的選擇性比較 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d904b279757e034050b79e16c1c1d61382e54746
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276649"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>本機專案資料夾與原始檔控制存放區的選擇性比較
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

