---
title: 保存 MSBuild 專案檔中的資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7772f633c44c50b24995b7cc8a3f2f8bbbb01863
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726058"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>在 MSBuild 專案檔中保存資料
專案子類型可能需要將特定類型的資料保存在專案檔中，以供稍後使用。 專案子類型會使用專案檔持續性，以符合下列需求：

1. 保存用於建立專案之部分的資料。 （如需 Microsoft Build Engine 的詳細資訊，請參閱[MSBuild](../../msbuild/msbuild.md)）。組建相關資訊可以是：

    1. 與設定無關的資料。 也就是，儲存在具有空白或遺失條件之 MSBuild 元素中的資料。

    2. 與設定相關的資料。 也就是儲存在 MSBuild 專案中的資料，其適用于特定專案設定。 例如:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. 保存與組建無關的資料。 這項資料可以用不是根據 XML 架構進行驗證的自由格式 XML 來表示。

    1. 與設定無關的資料。

    2. 與設定相關的資料。

## <a name="persisting-build-related-information"></a>保存組建相關資訊
 可用於建立專案的資料持續性會透過 MSBuild 來處理。 MSBuild 系統會維護組建相關資訊的主資料表。 專案子類型會負責存取此資料，以取得和設定屬性值。 專案子類型也可以藉由加入要保存的其他屬性，以及移除屬性，使其不會保存，來增強組建相關的資料表。

 若要修改 MSBuild 資料，專案子類型會負責從基底專案系統透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 來抓取 MSBuild 屬性物件。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 是在核心專案系統上實作為介面，並藉由執行 `QueryInterface` 來對其進行匯總專案子類型查詢。

 下列程式概述使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 移除屬性的步驟。

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>若要從 MSBuild 專案檔中移除屬性

1. 呼叫專案子類型 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 上的 `QueryInterface`。

2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>，`pszPropName` 設定為您要移除的屬性。

### <a name="persisting-non-build-related-information"></a>保存非組建相關資訊
 不重要的專案檔中的資料持續性會透過 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 來處理。

 您可以在主要 `project subtype aggregator` 物件、`project subtype project configuration` 物件或兩者上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>。

 下列重點概述有關非組建相關資訊持續性的主要概念。

- 基底專案會呼叫主要專案子類型（也就是最外層的專案子類型）匯總工具物件，以載入和儲存設定獨立的資料，並在專案子類型專案設定物件上呼叫，以載入或儲存設定相依的data.

- 基底專案會針對每個層級的專案子類型匯總，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 多次的方法，並傳遞每個層級的 GUID。

- 基底專案會傳遞或接收專屬於特定專案子類型的 XML 片段，並使用此機制做為在匯總層級之間保存狀態的方式。

- 基底專案會呼叫最外層專案子類型的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementation 傳入 GUID。 如果 GUID 屬於最外層的專案子類型，它會處理呼叫本身;否則，它會將呼叫委派給內部專案子類型，依此類推，直到找到 GUID 對應的專案子類型為止。

- 專案子類型也可以在委派內部專案子類型的呼叫之前或之後修改 XML 片段。 下列範例顯示的是專案檔的摘錄，其中包含專案子類型特有屬性的檔案名，會傳遞至該專案子類型。

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>請參閱
- [專案子類型](../../extensibility/internals/project-subtypes.md)