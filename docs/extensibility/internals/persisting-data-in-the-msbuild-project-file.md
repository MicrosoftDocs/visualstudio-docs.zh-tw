---
title: MSBuild 專案檔中保存的資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 362a4c09e3e0c732d939cf42b926b003260c4b00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988118"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>在 MSBuild 專案檔中保存資料
專案子類型可能需要將子類型特定的資料保存在專案檔，以供稍後使用。 專案子類型會使用專案檔案持續性，以符合下列需求：  
  
1.  保存資料做為建置專案的一部分。 (如需有關 Microsoft Build Engine 的詳細資訊，請參閱[MSBuild](../../msbuild/msbuild.md)。)可以與組建相關的資訊：  
  
    1.  組態無關的資料。 也就是儲存在具有空白或遺漏條件的 MSBuild 項目中的資料。  
  
    2.  設定相依的資料。 也就是儲存在會針對特定的專案組態的條件式的 MSBuild 項目中的資料。 例如:   
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  將不會與組建相關的資料保存。 這項資料可以以自由形式的 XML，不會針對 XML 結構描述進行驗證。  
  
    1.  組態無關的資料。  
  
    2.  設定相依的資料。  
  
## <a name="persisting-build-related-information"></a>保存與組建相關的資訊  
 適用於建置的專案資料的持續性是透過 MSBuild 處理。 MSBuild 系統會維護主要組建的相關資訊的資料表。 專案子類型會負責存取此資料來取得和設定屬性值。 專案子類型也可以加強組建相關的資料表，藉由新增其他屬性，以保存和移除屬性，因此不會保存。  
  
 若要修改的 MSBuild 資料，專案子類型會負責從基礎專案系統，透過擷取 MSBuild 屬性物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 已實作的介面核心專案系統和彙總的專案子類型查詢上，執行`QueryInterface`。  
  
 下列程序概述的步驟移除屬性，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>若要移除的 MSBuild 專案檔中的屬性  
  
1.  呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>的專案子類型。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>與`pszPropName`設定您想要移除的屬性。  
  
### <a name="persisting-non-build-related-information"></a>保存非建置相關的資訊  
 持續性的專案檔中建置並不重要的資料透過處理<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>。  
  
 您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>主要`project subtype aggregator`物件，`project subtype project configuration`物件，或兩者。  
  
 以下概述的非建置相關資訊的持續性有關的主要概念。  
  
-   基底專案主要專案子類型 （也就是最外層的專案子類型） 彙總工具在物件上呼叫以載入和儲存設定獨立的資料，而且它會呼叫上專案子類型的專案組態物件，以載入或儲存組態相依資料。  
  
-   基底的專案呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>多個時間的專案子類型的彙總，每個層級，並傳遞每個層級的 GUID。  
  
-   基底的專案會傳遞或接收的 XML 片段專屬於特定專案子類型，並彙總層級之間保存的狀態這種使用這項機制。  
  
-   基底的專案呼叫的最外層的專案子類型<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>傳入 GUID 的實作。 如果 GUID 屬於最外層的專案子類型，它會處理呼叫本身;否則它會委派呼叫內部專案子類型，並依此類推，直到找到 GUID 對應於專案子類型。  
  
-   專案子類型也可以修改 XML 片段，它會委派至內部專案子類型呼叫前後。 下列範例摘錄自專案檔，其中包含特定專案子類型，屬性的檔案名稱會傳遞至該專案子類型。  
  
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
 [專案子類型](../../extensibility/internals/project-subtypes.md)