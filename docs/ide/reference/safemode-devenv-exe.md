---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c8748a6dadaee41a5e615742715a92240b74ab8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，並且只載入預設環境和服務。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>備註  
 此參數會在啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 時防止載入所有協力廠商 VSPackages，因而確保穩定執行。  
  
## <a name="description"></a>描述  
 下列範例會以安全模式啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="code"></a>程式碼  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)