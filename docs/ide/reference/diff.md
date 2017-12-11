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
ms.openlocfilehash: d38ef64a370b11c2695ea1e03d2e3ceead7cb63c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="diff"></a>/Diff
比較兩個檔案。 這些差異會顯示在特殊 Visual Studio 視窗中。  
  
## <a name="syntax"></a>語法  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]  
```  
  
## <a name="arguments"></a>引數  
 `SourceFile`  
 必要項。 要比較之第一個檔案的完整路徑和名稱。  
  
 `TargetFile`  
 必要項。 要比較之第二個檔案的完整路徑和名稱  
  
 `SourceDisplayName`  
 選擇項。 第一個檔案的顯示名稱。  
  
 `TargetDisplayName`  
 選擇項。 第二個檔案的顯示名稱。