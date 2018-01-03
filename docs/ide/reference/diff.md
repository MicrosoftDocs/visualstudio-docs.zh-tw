---
title: -Diff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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