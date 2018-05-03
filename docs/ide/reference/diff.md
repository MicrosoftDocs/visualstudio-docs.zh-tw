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
ms.openlocfilehash: 81c70c238a4503fbd05249ef6522cf020c00221c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="diff"></a>/Diff
比較兩個檔案。 這些差異會顯示在特殊 Visual Studio 視窗中。

## <a name="syntax"></a>語法

```
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