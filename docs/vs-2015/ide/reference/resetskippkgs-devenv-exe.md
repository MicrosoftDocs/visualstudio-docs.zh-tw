---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 59bde318995ed8b66637a2220ae1817db2a1e800
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834674"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
清除所有選項，以略過載入使用者新增的 VSPackage，避免載入有問題的 VSPackage，然後啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## <a name="remarks"></a>備註  
 SkipLoading 標記的存在會停用 VSPackage 的載入，清除標記則會重新啟用載入 VSPackage。  
  
## <a name="example"></a>範例  
 下列範例會清除所有的 SkipLoading 標記。  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
