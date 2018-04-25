---
title: -Diff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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