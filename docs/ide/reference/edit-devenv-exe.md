---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5588d5dbf86039273854ddc372d1bbe096dad70b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948136"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
在現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體中開啟指定的檔案。

## <a name="syntax"></a>語法

```cmd
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>引數
 `file1`

 選擇性。 要在現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體中開啟的檔案。 如果沒有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體，則會建立具有簡化視窗版面配置的新執行個體，而且會在新執行個體中開啟 `file1`。

 `file2`

 選擇性。 要在現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體中開啟的一或多個其他檔案。

## <a name="remarks"></a>備註
 如果未指定任何檔案，而且具有現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體，則現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體會變成焦點。 如果未指定任何檔案，而且沒有現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體，則會建立具有簡化視窗版面配置的新 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體。

 如果現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體處於強制回應狀態 (例如，如果開啟[選項對話方塊](../../ide/reference/options-dialog-box-visual-studio.md))，則會在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 結束強制回應狀態時，於現有執行個體中開啟檔案。

## <a name="example"></a>範例
 此範例會在現有 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體中開啟 `MyFile.cs` 檔案中或在新 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行個體檔中開啟 (如果沒有執行個體)。

```cmd
devenv /edit MyFile.cs
```

## <a name="see-also"></a>請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)