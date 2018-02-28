---
title: "MSBuild 專案檔中的資料保存 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b2bb73602a6cba07fe9cbde4ddae4219f5a2b350
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild 專案檔中的保存資料
專案子類型可能需要將特定子類型的資料保存在專案檔，以供稍後使用。 專案子類型會使用專案檔的持續性符合下列需求：  
  
1.  保存資料做為建置專案的一部分。 (如需有關 Microsoft Build Engine 的詳細資訊，請參閱[MSBuild](../../msbuild/msbuild.md)。)與組建相關的資訊可以執行下列動作：  
  
    1.  組態無關的資料。 也就是儲存在 MSBuild 項目，並設定空白或遺漏條件的資料。  
  
    2.  組態相關資料。 也就是儲存在特定專案組態由 MSBuild 項目中的資料。 例如:   
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  保存與建置不相關的資料。 這項資料可以自由格式不會驗證 XML 結構描述的 xml 表示。  
  
    1.  組態無關的資料。  
  
    2.  組態相關資料。  
  
## <a name="persisting-build-related-information"></a>保存與組建相關的資訊  
 適用於建置專案的資料持續性是透過 MSBuild 處理。 MSBuild 系統會維護主要與組建相關資訊的資料表。 專案子類型會負責存取這項資料來取得和設定屬性值。 專案子類型也可以擴大與建置相關的資料表，加入要保存的其他屬性，以及移除屬性，因此不會保存。  
  
 若要修改的 MSBuild 資料，專案子類型會負責從基底專案系統，透過擷取 MSBuild 屬性物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>已實作的介面核心專案系統和彙總的專案子類型查詢上，執行`QueryInterface`。  
  
 下列程序概述的步驟，移除屬性，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>。  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>若要從 MSBuild 專案檔中移除屬性  
  
1.  呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>專案子類型。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A>與`pszPropName`設為您想要移除的屬性。  
  
### <a name="persisting-non-build-related-information"></a>保存非組建的相關的資訊  
 專案檔中建置並不重要的資料持續性透過處理<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>。  
  
 您可以實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>在主要`project subtype aggregator`物件`project subtype project configuration`物件，或兩者。  
  
 下列各點概述非組建的相關資訊的持續性有關的主要概念。  
  
-   基底的專案呼叫主要專案子類型 （也就是最外層的專案子類型） 彙總工具物件上以載入和儲存設定獨立的資料，它會載入或儲存組態相關專案子類型的專案組態物件上呼叫資料。  
  
-   基底的專案呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>多時間的每個層級的專案子類型的彙總，並傳遞每個層級的 GUID。  
  
-   基底專案傳遞，或接收的 XML 片段專用於特定專案子類型，並使用這項機制，做為保存的狀態，彙總層級之間的方式。  
  
-   基底的專案呼叫的最外層的專案子類型<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>傳入 GUID 的實作。 如果 GUID 所屬的最外層的專案子類型，它會處理呼叫本身;否則它會委派呼叫內部專案子類型，並依此類推，直到找到 GUID 對應於專案子類型。  
  
-   專案子類型也可以修改的 XML 片段之前或之後，它會委派至內部專案子類型呼叫。 下列範例摘錄自專案檔，其中包含特定專案子類型的屬性的檔案名稱傳遞至該專案子類型。  
  
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
 [專案子類型](../../extensibility/internals/project-subtypes.md)