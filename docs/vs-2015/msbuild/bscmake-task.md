---
title: BscMake 工作 | Microsoft Docs
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
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3ae418c8448fc2ebe4f5b2af0a8c713458988fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498868"
---
# <a name="bscmake-task"></a>BscMake 工作
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[BscMake 工作](https://docs.microsoft.com/visualstudio/msbuild/bscmake-task)。  
  
  
重要]
>  Visual Studio IDE 已不再使用 bscmake。 從 Visual Studio 2008 起，瀏覽資訊會自動儲存在方案資料夾的 .sdf 檔案中。  
  
 包裝 Microsoft Browse Information Maintenance Utility 工具 (bscmake.exe)。  bscmake.exe 工具會從編譯期間所建立的來源瀏覽器檔案 (.sbr) 建置瀏覽資訊檔 (.bsc)。 使用物件瀏覽器來檢視 .bsc 檔案。 如需詳細資訊，請參閱 [BSCMAKE 參考](http://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13)。  
  
## <a name="parameters"></a>參數  
 下表描述 **BscMake** 工作的參數。 大部分的工作參數會對應至命令列選項。  
  
|參數|描述|  
|---------------|-----------------|  
|**AdditionalOptions**|選擇性的 **String** 參數。<br /><br /> 選項的清單，如命令列上所指定。 例如，"/*option1* /*option2* /*option#*"。 使用這個參數來指定任何其他 **BscMake** 工作參數未表示的選項。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)中的選項。|  
|**OutputFile**|選擇性的 **String** 參數。<br /><br /> 指定將會覆寫預設輸出檔案名稱的檔案名稱。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)中的 **/o** 選項。|  
|**PreserveSBR**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，會強制執行非累加建置。 無論 .bsc 檔案是否存在，都執行完整、非累加建置，並防止 .sbr 檔被截斷。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)中的 **/n** 選項。|  
|**Sources**|選擇性的 **ITaskItem[]** 參數。<br /><br /> 定義工作可以耗用和發出的 MSBuild 來源檔案項目的陣列。|  
|**SuppressStartupBanner**|選擇性的 **Boolean** 參數。<br /><br /> 如果是 `true`，當工作開始時，會防止顯示著作權和版本號碼訊息。<br /><br /> 如需詳細資訊，請參閱 [BSCMAKE 選項](http://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)中的 **/NOLOGO** 選項。|  
|**TrackerLogDirectory**|選擇性的 **String** 參數。<br /><br /> 指定追蹤器記錄檔的目錄。|  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [工作參考](../msbuild/msbuild-task-reference.md)



