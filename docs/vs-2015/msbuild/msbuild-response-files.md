---
title: MSBuild 回應檔 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71fdc29db3e2af66c85637648bb0703e7f7d80c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486006"
---
# <a name="msbuild-response-files"></a>MSBuild 回應檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[MSBuild 回應檔](https://docs.microsoft.com/visualstudio/msbuild/msbuild-response-files)。  
  
  
回應檔 (.rsp) 是包含 MSBuild.exe 命令列參數的文字檔。 每個參數可位於單獨一行，或所有參數可位於同一行。 註解行前面會加上 **#** 符號。 **@** 參數可用來將其他回應檔案傳遞給 MSBuild.exe。  
  
 自動回應檔是 MSBuild.exe 在建置專案時會自動使用的特殊 .rsp 檔案。 MSBuild.rsp 必須與 MSBuild.exe 位於相同目錄中，否則系統會找不到這個檔案。 您可以編輯此檔案以指定 MSBuild.exe 的預設命令列參數。 好比說，如果您每次建置專案時都使用相同的記錄器，則可以將 **/logger** 參數新增至 MSBuild.rsp，MSBuild.exe 即會在每次建置專案時使用這個記錄器。  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../msbuild/msbuild-reference.md)   
 [命令列參考](../msbuild/msbuild-command-line-reference.md)



