---
title: 排序、 篩選和分組在 XML 結構描述總管中
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740fd46d453a6e6a51285d418374d036d83bc598
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808102"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>排序、 篩選和群組 （XML 結構描述總管）

本主題描述的選項，都是透過**排序、 篩選與分組選項**上的功能表**XML 結構描述總管**工具列。

## <a name="filter-options"></a>篩選選項

 以下是可用的篩選選項。 根據預設，**顯示命名空間**並**顯示結構描述檔案**選取選項。

- **顯示命名空間**。

- **顯示結構描述檔案**。

- **顯示撰寫 (sequence/choice/all)**。

## <a name="sorting-options"></a>排序選項

 以下是可用的排序選項。 預設值是**依類型排序**。 **排序依據**選項不適用於檔案與命名空間。

- **依類型排序**。

- **依名稱排序**。

- **文件順序**。

### <a name="sort-by-type"></a>依類型排序

 當**依類型排序**選取選項，全域節點都會依照下列順序。 然後，節點會在每個群組內部依字母順序排序。

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

 當**依名稱排序**選取選項，全域節點都會依照下列順序：

1. `import` 節點 (依照命名空間的字母順序)。

2. `include` 節點 (依照 `schemaLocation` 屬性的字母順序)。

3. `redefine` 節點 (依照 `schemaLocation` 屬性的字母順序)。

4. 其他全域節點 (依照字母順序)。

### <a name="document-order"></a>文件順序

 **文件順序**選項時，可以使用**顯示結構描述檔案**選項。 當**文件順序**選取時，全域節點會顯示在其出現在結構描述檔案中的順序。

## <a name="persisting-sortfilter-options"></a>持續排序/篩選選項

 無論變更設定時開啟哪一個方案或檔案，排序、篩選與群組選項都會儲存至每位使用者的登錄。