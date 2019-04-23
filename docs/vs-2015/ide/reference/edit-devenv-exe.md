---
title: -Edit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c4dabbb0c21fd6b4cabb01655485c8158662adb2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667270"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體中開啟指定的檔案。  
  
## <a name="syntax"></a>語法  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## <a name="arguments"></a>引數  
 `file1`  
 選擇性。 要在現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體中開啟的檔案。 如果沒有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，則會建立具有簡化視窗版面配置的新執行個體，而且會在新執行個體中開啟 `file1`。  
  
 `file2`  
 選擇性。 要在現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體中開啟的一或多個其他檔案。  
  
## <a name="remarks"></a>備註  
 如果未指定任何檔案，而且具有現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，則現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體會變成焦點。 如果未指定任何檔案，而且沒有現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，則會建立具有簡化視窗版面配置的新 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體。  
  
 如果現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體處於強制回應狀態 (例如，如果開啟[選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md))，則會在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 結束強制回應狀態時，於現有執行個體中開啟檔案。  
  
## <a name="example"></a>範例  
 此範例會在現有 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體中開啟 `MyFile.cs` 檔案中或在新 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體檔中開啟 (如果沒有執行個體)。  
  
```  
devenv /edit MyFile.cs  
```  
  
## <a name="see-also"></a>請參閱  
 [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
