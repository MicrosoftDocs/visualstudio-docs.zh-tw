---
title: -Edit (devenv.exe)
description: 瞭解如何使用編輯 devenv 命令列參數，在現有的 Visual Studio 實例中開啟指定的檔案。
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 845f83d2078999e3b3e32e048f9a3fa716300b19
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040585"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

在現有 Visual Studio 執行個體中開啟指定的檔案。

## <a name="syntax"></a>語法

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>引數

- *1*

  選擇性。 要在現有 Visual Studio 執行個體中開啟的檔案。 如果沒有任何 Visual Studio 執行個體存在，即會建立具有簡易視窗配置的新執行個體，而工具會在新的執行個體中開啟 *File1*。

- *FileN*

  選擇性。 要在現有 Visual Studio 執行個體中開啟的一或多個其他檔案。

## <a name="remarks"></a>備註

未指定檔案時，現有 Visual Studio 執行個體就會收到焦點。 如果未指定任何檔案，而且沒有任何 Visual Studio 執行個體存在，工具就會建立具有簡易視窗配置的執行個體。

如果現有 Visual Studio 執行個體處於強制回應狀態，該檔案即會在 Visual Studio 結束強制回應時，於現有執行個體中開啟。 例如，這種情況可能會在開啟 [[選項] 對話方塊](../../ide/reference/options-dialog-box-visual-studio.md)時發生。

如果開啟 Visual Studio 的多個執行個體，檔案會在最近開啟的執行個體中開啟。

## <a name="example"></a>範例

第一個範例會在現有 Visual Studio 執行個體中開啟 `MyFile.cs` 檔案。 如果 Visual Studio 執行個體不存在，工具就會在新的執行個體中開啟該檔案。 第二個範例很類似，不同之處在於它會開啟三個檔案，而不只開啟一個檔案。

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
