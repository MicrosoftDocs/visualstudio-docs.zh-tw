---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72630bd7c16c3830fecddc34a71b7ea1e4cf382c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)