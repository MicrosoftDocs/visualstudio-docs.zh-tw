---
title: 在 MSBuild 專案檔中保存資料 |Microsoft Docs
description: 瞭解如何將資料保存在專案檔中，並使用 IPersistXMLFragment 來維護專案檔中專案子類型匯總層級的資料。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 20c6d79e6ea59b4993b4d6bfc5e165bdd952a3f9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878075"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>在 MSBuild 專案檔中保存資料
專案子類型可能需要將子類型專屬的資料保存到專案檔中，以供稍後使用。 專案子類型會使用專案檔持續性來符合下列需求：

1. 保存在建立專案時使用的資料。  (如需 Microsoft Build Engine 的詳細資訊，請參閱 [MSBuild](../../msbuild/msbuild.md)。 ) 組建相關資訊可以：

    1. 與設定無關的資料。 也就是說，儲存在具有空白或遺漏條件之 MSBuild 元素中的資料。

    2. 與設定相依的資料。 也就是說，儲存在以特定專案設定條件下之 MSBuild 元素中的資料。 例如：

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. 保存與組建無關的資料。 這項資料可以用不是針對 XML 架構進行驗證的自由格式 XML 來表示。

    1. 與設定無關的資料。

    2. 與設定相依的資料。

## <a name="persisting-build-related-information"></a>保存 Build-Related 資訊
 用來建立專案的資料持續性，是透過 MSBuild 來處理。 MSBuild 系統會維護組建相關資訊的主表。 專案子類型負責存取此資料，以取得和設定屬性值。 專案子類型也可以增強與組建相關的資料表，方法是新增要保存的其他屬性，並移除屬性，使其不會保存。

 若要修改 MSBuild 資料，專案子類型會負責從基底專案系統透過來取得 MSBuild 屬性物件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 是在核心專案系統上執行的介面，並藉由執行來為其匯總專案子類型查詢 `QueryInterface` 。

 下列程式概述使用移除屬性的步驟 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 。

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>從 MSBuild 專案檔案移除屬性

1. `QueryInterface`在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 專案子類型上呼叫。

2. 呼叫， <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> 並 `pszPropName` 將設定為您要移除的屬性。

### <a name="persisting-non-build-related-information"></a>保存非組建的相關資訊
 不重要的專案檔中的資料持續性，是透過進行處理 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 。

 您可以 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 在主要 `project subtype aggregator` 物件、 `project subtype project configuration` 物件或兩者上執行。

 下列各點概述有關非組建相關資訊之持續性的主要概念。

- 基底專案會呼叫主要專案子類型 (也就是最外層的專案子類型) 匯總工具物件來載入及儲存設定獨立的資料，並在專案子類型專案設定物件上呼叫，以載入或儲存設定相依的資料。

- 基底專案會 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 針對每個層級的專案子類型匯總呼叫多個時間的方法，並傳遞每個層級的 GUID。

- 基底專案會傳遞或接收特定專案子類型專用的 XML 片段，並使用此機制來保存匯總層級之間的狀態。

- 基底專案會呼叫在 GUID 中傳遞的最外層專案子類型的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 實作為。 如果 GUID 屬於最外層的專案子類型，則會處理呼叫本身;否則，它會將呼叫委派給內部專案子類型，依此類推，直到找到 GUID 對應的專案子類型為止。

- 專案子類型也可以在將呼叫委派給內部專案子類型之前或之後修改 XML 片段。 下列範例顯示從專案檔摘錄的專案檔，其中包含專案子類型特定屬性的檔案名，會傳遞至該專案子類型。

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
