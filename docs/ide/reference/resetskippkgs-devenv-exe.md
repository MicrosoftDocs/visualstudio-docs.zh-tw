---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f84b4a8f73d378629edcf862f1aa53aa478fa1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
清除所有選項，以略過載入使用者新增的 VSPackage，避免載入有問題的 VSPackage，然後啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
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