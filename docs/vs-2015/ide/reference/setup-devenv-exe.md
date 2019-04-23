---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6e5bbbf3a1a9601a46aa9d3080f0d20583b43d22
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670234"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
