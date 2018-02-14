---
title: "MSBuild 回應檔 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7520a9f51f0d9420039728a75e84d4ed16583738
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-response-files"></a>MSBuild 回應檔
回應檔 (.rsp) 是包含 MSBuild.exe 命令列參數的文字檔。 每個參數可位於單獨一行，或所有參數可位於同一行。 註解行前面會加上 **#** 符號。 **@** 參數可用來將其他回應檔案傳遞給 MSBuild.exe。  
  
 自動回應檔是 MSBuild.exe 在建置專案時會自動使用的特殊 .rsp 檔案。 MSBuild.rsp 必須與 MSBuild.exe 位於相同目錄中，否則系統會找不到這個檔案。 您可以編輯此檔案以指定 MSBuild.exe 的預設命令列參數。 好比說，如果您每次建置專案時都使用相同的記錄器，則可以將 **/logger** 參數新增至 MSBuild.rsp，MSBuild.exe 即會在每次建置專案時使用這個記錄器。  
  
## <a name="see-also"></a>請參閱  
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [命令列參考](../msbuild/msbuild-command-line-reference.md)