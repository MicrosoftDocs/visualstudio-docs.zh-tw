---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1e8f81e61121fd6779cc0f0ebdbd166bf0c27c6f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
將方案檔和其所有專案檔或指定的專案檔更新成這些檔案的目前 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 格式。  
  
## <a name="syntax"></a>語法  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>引數  
 `SolutionFile`  
 如果您要升級整個方案和其專案，則為必要項目。 方案檔的路徑和名稱。 您可以只輸入方案檔的名稱，或是方案檔的完整路徑和名稱。 如果命名的資料夾或檔案還未存在，則會予以建立。  
  
 `ProjectFile`  
 如果您要升級單一專案，則為必要項目。 方案中專案檔的路徑和名稱。 您可以只輸入專案檔的名稱，或是專案檔的完整路徑和名稱。 如果命名的資料夾或檔案還未存在，則會予以建立。  
  
## <a name="remarks"></a>備註  
 備份會自動建立並複製到在目前目錄中建立且名為 Backup 之目錄的備份。  
  
 必須先簽出原始檔控制的方案或專案，才能進行升級。  
  
 使用 `/upgrade` 切換參數時，不會啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 在方案或專案之開發語言的升級報表中可以看到升級結果。 不會傳回任何錯誤或使用方式資訊。 如需在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中升級專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)。  
  
## <a name="example"></a>範例  
 這個範例會在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 方案的預設資料夾中升級名為 "MyProject.sln" 的方案檔。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
