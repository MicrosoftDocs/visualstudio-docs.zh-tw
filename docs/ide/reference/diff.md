---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cbf0f8f9fa2e97908e2ae13e3961382a7250a91
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="diff"></a>/Diff
比較兩個檔案。 這些差異會顯示在特殊 Visual Studio 視窗中。

## <a name="syntax"></a>語法

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>引數
 `SourceFile`

 必要。 要比較之第一個檔案的完整路徑和名稱。

 `TargetFile`

 必要。 要比較之第二個檔案的完整路徑和名稱

 `SourceDisplayName`

 選擇性。 第一個檔案的顯示名稱。

 `TargetDisplayName`

 選擇性。 第二個檔案的顯示名稱。