---
title: 在建置大型專案時有效使用記憶體 | Microsoft Docs
description: 瞭解 MSBuild 如何在建立大型專案時，自動管理記憶體，例如卸載較舊的版本，以及抓取快取。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965898"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>在建置大型專案時有效使用記憶體

大型專案通常會包含許多子專案和其他相依性，這可能會在建置時耗用大量系統記憶體。 可用系統記憶體減少時，系統效能也可能會降低。 舊版的 MSBuild 專案會保留在記憶體中。 3.5 版中移除了舊版專案，但在快取中保留了建置結果以供日後擷取之用。

 4.0 版會自動處理此記憶體管理，並儲存專案；而不需要使用 `UnloadProjectsOnCompletion` 和 `UseResultsCache` 這類屬性。

### <a name="see-also"></a>另請參閱

- [平行建立多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
