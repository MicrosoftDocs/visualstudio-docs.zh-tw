---
title: "在建置大型專案時有效使用記憶體 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1e78afd0f76839d170f12cf4315610c183899fff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>在建置大型專案時有效使用記憶體
大型專案通常會包含許多子專案和其他相依性，而且這些可能會在建置時間耗用大量系統記憶體。 可用系統記憶體減少時，系統效能也可能會降低。 舊版 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案會保留在記憶體中；而在 3.5 版中則會移除專案，但它會將建置結果保留在快取中，以供稍後擷取。  
  
 4.0 版會自動處理此記憶體管理，並儲存專案；而不需要使用 `UnloadProjectsOnCompletion` 和 `UseResultsCache` 這類屬性。  
  
## <a name="see-also"></a>請參閱  
 [同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)