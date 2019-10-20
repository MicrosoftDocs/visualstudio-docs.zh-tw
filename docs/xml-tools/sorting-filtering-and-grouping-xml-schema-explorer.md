---
title: 在 XML 架構瀏覽器中排序、篩選和分組
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf9226f3b491a39c7ef5936667cabd789c6a457
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604585"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>排序、篩選和群組（XML 架構瀏覽器）

本主題描述透過**XML 架構瀏覽器**工具列上的 [**排序]、[篩選] 和 [群組選項**] 功能表所提供的選項。

## <a name="filter-options"></a>篩選選項

以下是可用的篩選選項。 預設會選取 [**顯示命名空間**] 和 [**顯示架構**檔案] 選項。

- **顯示命名空間**。

- **顯示架構**檔案。

- **顯示撰寫（sequence/choice/all）** 。

## <a name="sorting-options"></a>排序選項

以下是可用的排序選項。 預設值為 [**依類型排序**]。 [**排序依據**] 選項不會套用至檔案和命名空間。

- **依類型排序**。

- **依名稱排序**。

- **檔順序**。

### <a name="sort-by-type"></a>依類型排序

選取 [**依類型排序**] 選項時，全域節點會依照下列順序排序。 然後，節點會在每個群組內部依字母順序排序。

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

選取 [**依名稱排序**] 選項時，全域節點會依照下列順序排序：

1. `import` 節點 (依照命名空間的字母順序)。

2. `include` 節點 (依照 `schemaLocation` 屬性的字母順序)。

3. `redefine` 節點 (依照 `schemaLocation` 屬性的字母順序)。

4. 其他全域節點 (依照字母順序)。

### <a name="document-order"></a>文件順序

選取 [**顯示架構**檔案] 選項時，可以使用 [檔**順序**] 選項。 選取 [**檔順序**] 時，全域節點會依照出現在架構檔案中的順序顯示。

## <a name="persisting-sortfilter-options"></a>持續排序/篩選選項

無論變更設定時開啟哪一個方案或檔案，排序、篩選與群組選項都會儲存至每位使用者的登錄。