---
title: 排序、篩選和分組
description: 透過 XML 架構瀏覽器工具列上的 [排序]、[篩選] 和 [群組選項] 功能表，瞭解可用的選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98ead8b2f0ddc7edc84449c3f80deeb7598fdfab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849758"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>排序、篩選和分組 (XML 架構瀏覽器) 

本主題說明可透過 **XML 架構瀏覽器** 工具列上的 [**排序]、[篩選] 和 [群組選項**] 功能表使用的選項。

## <a name="filter-options"></a>篩選選項

以下是可用的篩選選項。 預設會選取 [ **顯示命名空間** ] 和 [ **顯示架構** 檔案] 選項。

- **顯示命名空間**。

- **顯示架構** 檔案。

- **顯示撰寫 (sequence/choice/all)**。

## <a name="sorting-options"></a>排序選項

以下是可用的排序選項。 預設值是 **依類型排序**。 [**排序依據**] 選項不適用於檔案和命名空間。

- **依類型排序**。

- **依名稱排序**。

- **檔順序**。

### <a name="sort-by-type"></a>依類型排序

選取 [ **依類型排序** ] 選項時，全域節點會依下列順序排序。 然後，節點會在每個群組內部依字母順序排序。

1. `import` 節點。

2. `include` 節點。

3. `redefine` 節點。

4. `attribute` 節點。

5. `attributeGroup` 節點。

6. `complexType` 節點。

7. `simpleType` 節點。

8. `element` 節點。

9. `group` 節點。

### <a name="sort-by-name"></a>依名稱排序

選取 [ **依名稱排序** ] 選項時，全域節點會依下列順序排序：

1. `import` 節點會依) 命名空間的字母順序 (。

2. `include` 節點 (依照 `schemaLocation` 屬性的字母順序)。

3. `redefine` 節點 (依照 `schemaLocation` 屬性的字母順序)。

4. 其他全域節點 (依照字母順序)。

### <a name="document-order"></a>文件順序

選取 [**顯示架構** 檔案] 選項時，可以使用 [**檔順序**] 選項。 選取 [ **檔順序** ] 時，全域節點會依照它們出現在架構檔案中的順序顯示。

## <a name="persisting-sortfilter-options"></a>保存排序/篩選選項

無論變更設定時開啟哪一個方案或檔案，排序、篩選與群組選項都會儲存至每位使用者的登錄。
