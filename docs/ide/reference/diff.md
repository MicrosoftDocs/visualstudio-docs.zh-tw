---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e69435a319a9730af846a912cb3f90a12d4ac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945779"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

比較兩個檔案。 這些差異會顯示在特殊 Visual Studio 視窗中。

## <a name="syntax"></a>語法

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>引數

- *SourceFile*

  必要項。 要比較之第一個檔案的完整路徑和名稱。

- *TargetFile*

  必要項。 要比較之第二個檔案的完整路徑和名稱。

- *SourceDisplayName*

  選擇性。 第一個檔案的顯示名稱。

- *TargetDisplayName*

  選擇性。 第二個檔案的顯示名稱。

## <a name="remarks"></a>備註

如果已經開啟 IDE 的執行個體，則檔案比較會出現在目前 IDE 的索引標籤中。

## <a name="example"></a>範例

第一個範例會在不變更這兩個檔案之顯示名稱的情況下進行比較。 第二個範例會在變更這兩個檔案的顯示名稱時進行比較。 第三個和第四個範例會比較這兩個檔案，但只會將別名套用到第一個檔案或第二個檔案。

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>另請參閱

- [Devenv 命令列參數](../../ide/reference/devenv-command-line-switches.md)
