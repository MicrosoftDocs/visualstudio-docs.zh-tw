---
title: 匯入和匯出設定命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db7ccd5a4b8266122c2d295cde3cdcca87dc0576
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657830"
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
 執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[如何：在電腦與 Visual Studio 版本之間共用設定](http://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882)。  
  
## <a name="example"></a>範例  
 下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
