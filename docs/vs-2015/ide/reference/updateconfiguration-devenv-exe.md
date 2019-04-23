---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ffc9410d64f58fff771a0e9b251ee1131eaea5e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670026"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

通知 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件，並檢查 MEF 快取中的任何變更。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>備註  
 當您安裝 VSIX 套件時，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會自動執行此命令。 您應該在修補檔案之後執行 `devenv.exe /updateconfiguration`，讓 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 更新 MEF 快取。 這可讓您評估您的修正是否足夠。  
  
## <a name="example"></a>範例  
 下列命令列會使 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併系統上的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 套件，並檢查 MEF 快取中的任何變更。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
