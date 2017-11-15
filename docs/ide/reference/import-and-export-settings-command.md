---
title: "匯入和匯出設定命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61924f7d9430661114f1fecc36d585e2d223604b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="import-and-export-settings-command"></a>匯入和匯出設定命令
匯入、匯出或重設 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定。  
  
## <a name="syntax"></a>語法  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>參數  
 /export:`filename`  
 選擇項。 將目前的設定匯出至指定的檔案。  
  
 /import:`filename`  
 選擇項。 匯入指定檔案中的設定。  
  
 /reset  
 選擇項。 重設目前的設定。  
  
## <a name="remarks"></a>備註  
 執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[如何：在電腦與 Visual Studio 版本之間共用設定](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882)。  
  
## <a name="example"></a>範例  
 下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>另請參閱  
 [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)