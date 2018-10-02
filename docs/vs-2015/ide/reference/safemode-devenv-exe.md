---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 308dd7e81a35604bcd0f6f5eba517b850ace17ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491355"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[-/safemode (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/safemode-devenv-exe)。  
  
  
以安全模式啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，並且只載入預設環境和服務。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>備註  
 此參數會在啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 時防止載入所有協力廠商 VSPackages，因而確保穩定執行。  
  
## <a name="description"></a>描述  
 下列範例會以安全模式啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
## <a name="code"></a>程式碼  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)



