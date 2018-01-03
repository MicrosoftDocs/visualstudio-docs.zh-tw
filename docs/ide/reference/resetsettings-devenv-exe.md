---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
還原 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 預設值，並自動啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 選擇性地將設定重設為指定的 .vssettings 檔案。  
  
 第一次啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時，選取的設定檔即會決定預設值。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>引數  
 `SettingsFile`  
 要套用至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 .vssettings 檔完整路徑和名稱。  
  
 若要還原為一般開發設定的設定檔，請使用 `General`。  
  
## <a name="remarks"></a>備註  
 如果未指定任何 `SettingsFile`，下一次您啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時，系統將提示您選取預設的設定集合。  
  
## <a name="example"></a>範例  
 下列命令列會套用儲存在 `MySettings.vssettings` 檔案中的設定。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>請參閱  
 [將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)