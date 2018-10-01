---
title: -Setup (devenv.exe) | Microsoft Docs
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
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75b7fb7d812135014a8b868ef7590c99e83c15b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492092"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[-安裝程式 (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/setup-devenv-exe)。  
  
  
強制 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 合併所有來自可用 Vspackage 的資源中繼資料 (其描述功能表、工具列和命令群組)。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>備註  
 此參數不需使用引數。 一般來說，會將 `devenv /setup` 命令指定為安裝程序的最後一個步驟。 使用 `/setup` 參數時，不會啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
 您必須以系統管理員身分執行 `devenv` ，才能使用 [/setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) 和 [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) 參數。  
  
## <a name="example"></a>範例  
 這個範例會示範含 Vspackage 之 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 版本的最後一個安裝步驟 。  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>另請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)



