---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf58c25611fd52c6e8db8e8210101e1c80153275
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844534"
---
# <a name="diff"></a>/Diff
比較兩個檔案。 這些差異會顯示在特殊 Visual Studio 視窗中。

## <a name="syntax"></a>語法

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>引數
 `SourceFile`

 必要項。 要比較之第一個檔案的完整路徑和名稱。

 `TargetFile`

 必要項。 要比較之第二個檔案的完整路徑和名稱

 `SourceDisplayName`

 選擇性。 第一個檔案的顯示名稱。

 `TargetDisplayName`

 選擇性。 第二個檔案的顯示名稱。