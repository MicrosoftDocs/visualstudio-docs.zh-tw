---
title: 匯入和匯出設定命令 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2556b814059a80f2b93d0220de27cdbd8c051ea9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305561"
---
# <a name="import-and-export-settings-command"></a>匯入和匯出設定命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
匯入、匯出或重設 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 設定。  
  
## <a name="syntax"></a>語法  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>參數  
 /export:`filename`  
 選擇性。 將目前的設定匯出至指定的檔案。  
  
 /import:`filename`  
 選擇性。 匯入指定檔案中的設定。  
  
 /reset  
 選擇性。 重設目前的設定。  
  
## <a name="remarks"></a>備註  
 執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[如何：在電腦與 Visual Studio 版本之間共用設定](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882)。  
  
## <a name="example"></a>範例  
 下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)



