---
title: 在 MSBuild 專案檔中保留數據 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706689"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>在 MSBuild 專案檔中保存資料
專案子類型可能需要將特定於子類型的數據保存到專案檔中,以便以後使用。 專案子型態使用專案檔持久性來滿足以下要求:

1. 作為生成專案的一部分的持久化數據。 (有關 Microsoft 構建引擎的詳細資訊,請參閱[MSBuild](../../msbuild/msbuild.md).)與產生相關的資訊可以:

    1. 與配置無關的數據。 也就是說,存儲在 MSBuild 元素中的數據處於空白或缺失狀態。

    2. 與配置相關的數據。 也就是說,存儲在 MSBuild 元素中的數據是特定專案配置的條件。 例如：

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. 與生成無關的持久化數據。 此數據可以以非針對 XML 架構驗證的自由格式 XML 表示。

    1. 與配置無關的數據。

    2. 與配置相關的數據。

## <a name="persisting-build-related-information"></a>持久化與產生相關的資訊
 對構建專案有用的數據的持久性通過 MSBuild 進行處理。 MSBuild 系統維護生成相關信息的主表。 專案子類型負責訪問此數據以獲取和設置屬性值。 專案子類型還可以透過添加要保留的其他屬性和刪除屬性來增強與生成相關的數據表,以便不持久化這些屬性。

 要修改 MSBuild 資料,專案子類型負責透過從基礎項目系統檢索 MSBuild 屬性物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>是在核心項目系統上實現的介面,通過運行`QueryInterface`來聚合專案子類型查詢。

 以下過程概述了使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>刪除 屬性的步驟。

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>從 MSBuild 專案檔案中移除屬性

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>調用`QueryInterface`專案子類型。

2. 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>`pszPropName`設定為要刪除的屬性進行調用。

### <a name="persisting-non-build-related-information"></a>保留非產生相關資訊
 專案檔中重要的數據持久性並不重要,通過<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>處理。

 您可以在主<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>`project subtype aggregator`物件`project subtype project configuration`、物件或兩者上實現。

 以下幾點概述了有關非構建相關信息持久性的主要概念。

- 基本專案調用主專案子類型(即最外層專案子類型)聚合器物件來載入和保存配置獨立資料,並調用專案子類型專案配置物件來載入或保存與配置相關的數據。

- 基本專案調用每個級別的專案子<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>類型聚合的多次方法,並傳遞每個級別的 GUID。

- 基本項目傳遞或接收專用於特定專案子類型的 XML 片段,並使用此機制作為在聚合級別之間持久狀態的一種方式。

- 基專案調用最外層專案子類型在 GUID 中<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>傳遞的 實現。 如果 GUID 屬於最外層的專案子類型,它將處理調用本身;如果 GUID 屬於最外層的專案子類型,則處理調用本身。否則,它將調用委託給內部專案子類型,等等,直到找到 GUID 對應的專案子類型。

- 專案子類型還可以在將調用委託給內部專案子類型之前或之後修改 XML 片段。 下面的範例顯示了專案檔的摘錄,其中包含特定於專案子類型的屬性的檔的名稱將傳遞給該專案子類型。

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>另請參閱
- [專案子類型](../../extensibility/internals/project-subtypes.md)
