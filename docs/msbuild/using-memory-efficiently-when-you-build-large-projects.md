---
title: 在建置大型專案時有效使用記憶體 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631311"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>在建置大型專案時有效使用記憶體

大型專案通常會包含許多子專案和其他相依性，這可能會在建置時耗用大量系統記憶體。 可用系統記憶體減少時，系統效能也可能會降低。 較舊版本的 MSBuild 專案會保留在記憶體中。 3\.5 版中移除了舊版專案，但在快取中保留了建置結果以供日後擷取之用。

 4\.0 版會自動處理此記憶體管理，並儲存專案；而不需要使用 `UnloadProjectsOnCompletion` 和 `UseResultsCache` 這類屬性。

### <a name="see-also"></a>另請參閱

- [平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
