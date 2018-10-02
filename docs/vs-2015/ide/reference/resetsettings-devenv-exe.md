---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25697a792b0c48746a1d7840b8091ea718f5cdc7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488608"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[-ResetSettings (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetsettings-devenv-exe)。  
  
  
還原 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 預設值，並自動啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 選擇性地將設定重設為指定的 .vssettings 檔案。  
  
 第一次啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 時，選取的設定檔即會決定預設值。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>引數  
 `SettingsFile`  
 要套用至 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 的 .vssettings 檔完整路徑和名稱。  
  
 若要還原為一般開發設定的設定檔，請使用 `General`。  
  
## <a name="remarks"></a>備註  
 如果未指定任何 `SettingsFile`，下一次您啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 時，系統將提示您選取預設的設定集合。  
  
## <a name="example"></a>範例  
 下列命令列會套用儲存在 `MySettings.vssettings` 檔案中的設定。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)



