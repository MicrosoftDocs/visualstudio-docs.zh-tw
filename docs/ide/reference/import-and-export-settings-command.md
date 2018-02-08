---
title: "匯入和匯出設定命令 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3faa3d77a0aab8edfbe491b9df655931c2f6ed2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="import-and-export-settings-command"></a>匯入和匯出設定命令
匯入、匯出或重設 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定。  
  
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

執行此命令而不使用切換參數，會開啟 [匯入和匯出設定精靈]。 如需詳細資訊，請參閱[同步處理您的設定](../../ide/synchronized-settings-in-visual-studio.md)。

## <a name="example"></a>範例

下列命令會將目前的設定匯出至檔案 `MyFile.vssettings`。

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>另請參閱

[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)  
[Visual Studio 命令](../../ide/reference/visual-studio-commands.md)