---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b35026140b424da0f7fa71cb9e70b72c3dba243
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689651"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
